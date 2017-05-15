# HurmaDB

Work in progress.

# How to build, test and run

Install all dependencies:

```
sudo apt-get install g++ libpcre3-dev cmake python3-pip lcov wrk
```

Install and configure virtualenvwrapper:

```
sudo pip3 install virtualenv virtualenvwrapper
echo 'export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3' >> ~/.bashrc
echo 'source /usr/local/bin/virtualenvwrapper.sh' >> ~/.bashrc
bash
```

Create a virtualenv:

```
mkvirtualenv hurmadb
workon hurmadb
```

Install all Python dependencies into the virtualenv:

```
pip install -r requirements.txt
```

Build HurmaDB:

```
git clone https://github.com/afiskon/hurmadb.git
cd hurmadb
mkdir build
cd build
cmake ..
make -j2
```

Run tests:

```
make test
```

Run a benchmark:

```
./hurmadb 8080
curl -XPUT -d 'SomeRandomData123' localhost:8080/v1/kv/123 -D - -o -
wrk -t10 -c10 -d10s http://localhost:8080/v1/kv/123
```

Create a code coverage report:

```
./code-coverage.sh
```