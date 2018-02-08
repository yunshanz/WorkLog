# WorkLog
Keep Track of Work/Learn
2/7/2018
* pickle and dill cannot work correctly through exec() function if globals filed does not take dict with "__name__" in python.

Details:
>>> exec("import pickle\ndef a():\n    return 1\npickle.dump(a, open(\"D:/a\", \"wb\"))", globals())
>>> exec("import pickle\ndef a():\n    return 1\npickle.dump(a, open(\"D:/a\", \"wb\"))")
>>> exec("import pickle\ndef a():\n    return 1\npickle.dump(a, open(\"D:/a\", \"wb\"))", {})
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    File "<string>", line 4, in <module>
    _pickle.PicklingError: Can't pickle <function a at 0x00000204A82A4840>: it's not the same object as __main__.a

Currently, livy server cannot run the example code above because of the exec() behavior.
https://github.com/cloudera/livy/blob/89099b0d5d21c93932fb3fd4cfbe5533a851e7b1/repl/src/main/resources/fake_shell.py#L184

