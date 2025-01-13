# Consensus Compliance tests

## instructions
```
# using my repo currently, fc-compliance2 branch
git clone https://github.com/ericsson49/eth2.0-specs.git
cd eth2.0-specs
git checkout fc-compliance2

# setup python stuff

cd tests/generators/fork_choice_generated
python3 -m venv venv
. venv/bin/activate
# don't need it for tests themselves, but it's required to install requirements
pip install wheel

# turn on multiprocessing, do not have a command line switch at the moment
echo '\nGENERATOR_MODE = MODE_MULTIPROCESSING\n' >> ../../core/pyspec/eth2spec/gen_helpers/gen_base/settings.py

pip install -r requirements.txt

mkdir tests_tiny
python test_gen.py -o tests_tiny --fc-gen-config tiny/test_gen.yaml
```

