# Consensus Compliance Tests
This repository generates test cases for the Ethereum [Proof-of-Stake Consensus Spec](https://github.com/ethereum/consensus-specs) for fork choice compliance testing.

## Dependencies
- Python 3.12+
- System dependencies:
  - gcc
  - libsnappy-dev
  - libssl-dev
  - python3-dev
  - build-essential


## Test generation

### Manual
```bash
# Clone the eth2.0-specs repository
git clone -b fc-compliance2 https://github.com/ericsson49/eth2.0-specs.git
cd eth2.0-specs/tests/generators/fork_choice_generated

# Setup Python environment
python3 -m venv .venv
source .venv/bin/activate
pip3 install wheel setuptools && pip3 install -r requirements.txt

# Generate test cases
mkdir tests_tiny
python test_gen.py -o tests_tiny --fc-gen-multi-processing --fc-gen-config tiny/test_gen.yaml
```

### CI/CD
Test cases are generated on:
- Every push to `master`
- Pull requests
- Manual trigger via GitHub Actions UI

### Manual Workflow Trigger Options

You can manually trigger the workflow with custom parameters:

- **specs_repo**: eth2.0-specs repository URL (default: `ericsson49/eth2.0-specs`)
- **specs_ref**: Branch, tag or commit to use (default: `fc-compliance2`)
- **specs_path**: Local path to clone the specs (default: `eth2.0-specs`)

## Usage
Generated test cases are available as downloadable artifacts from the GitHub Actions workflow runs. 

1. Move into the scripts directory: `cd scripts`
2. Download and unzip the test cases from the workflow run
3. Install the requirements: `pip3 install ruamel.yaml==0.17.21 wheel setuptools && pip3 install -r requirements.txt`
4. Run the test cases with your fork choice implementation, e.g: `python3 test_generated_output.py -i tests_tiny`
