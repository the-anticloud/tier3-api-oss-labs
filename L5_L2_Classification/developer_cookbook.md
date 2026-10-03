# Developer Cookbook — api-oss-labs
**Stack:** Python 3.11, Docker (sandboxed), PAX 27B, pytest, AIOSS_FORMAT
**Domain:** Experimental Anticloud features: sandboxed testing environment for new capabilities
**License:** Apache-2.0 | **IP:** USPTO pending 2026, Anticloud FZ LLE

## Core Usage

```python
from api_oss_labs import ExperimentRunner
lab = ExperimentRunner(sandbox_dir='./lab_sandbox/', aioss_chain='./labs.aioss')
experiment = lab.run(
    name='flash_attention_v3_test',
    hypothesis='Flash Attention 3 increases throughput by 20% on T4',
    code_path='./experiments/flash_attn_v3.py'
)
print(f'Result: {experiment.result}, Promote: {experiment.should_promote}')
```

## AIOSS Chain Append

```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()

# After every api-oss-labs output:
chain_hash = aioss_append("./api_oss_labs.aioss",
                           result_bytes, "api-oss-labs")
```

## Performance & Integration

Performance: profile with api-oss-devtools. Benchmark with api-oss-analytics. Integration: all api-oss-labs operations are logged to api-oss-logging and audited by api-oss-compliance.
