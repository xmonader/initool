# initool

ini files are everywhere and `initool` gives you an easy way to manipulate your inifiles


## Usage
initool supports mainly 4 operations `show`, `get`, `set`, `rm`

show example
```
➜  /tmp cat sample.ini | initool show
[sec1]
key1 = val1

[sec2]
key2 = val2

[sec3]
key3 = val3
keyx = valx

➜ /tmp cat sample.ini | initool show --json
{"sec2": {"key2": "val2"}, "sec3": {"key3": "val3", "keyx": "valx"}, "sec1": {"key1": "val1"}}
```
`get` for getting a `key` or a complete `section`
```
➜  /tmp cat sample.ini | initool get sec1/key1
val1
➜  /tmp cat sample.ini | initool get sec1     
key1=val1

➜  /tmp cat sample.ini | initool get sec3
key3=val3
keyx=valx

➜  /tmp cat sample.ini | initool get sec3 --json
[["key3", "val3"], ["keyx", "valx"]]
```
`set` used to set the value of an option
```
➜  /tmp cat sample.ini | initool set sec3/keyx valz --json
{"sec1": {"key1": "val1"}, "sec2": {"key2": "val2"}, "sec3": {"key3": "val3", "keyx": "valz"}}
➜  /tmp cat sample.ini | initool set sec3/keyx valz 
[sec1]
key1 = val1

[sec2]
key2 = val2

[sec3]
key3 = val3
keyx = valz
```

`rm` used to remove option or section from the ini files
```
➜  /tmp cat sample.ini | initool rm sec3                  
[sec1]
key1 = val1

[sec2]
key2 = val2

➜  /tmp cat sample.ini | initool rm sec3/keyx
[sec1]
key1 = val1

[sec2]
key2 = val2

[sec3]
key3 = val3

```

## How to Install?
just `pip3 install initool`
or run `python3 setup.py sdist && python3 setup.py install` 