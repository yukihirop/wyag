
## init

```
./wyag init right
```

## cat-file

```
$ ../wyag cat-file commit 009d3055c1861fc618d4d0981d6ab119c6598bdc
tree aaa1770a0f8d8ddad8c81e009c6190baf7ed3926
parent e537175bbdf4cfeaf5e3f3c757e29ebb443b28aa
author yukihirop <te108186@gmail.com> 1578060335 +0900
committer yukihirop <te108186@gmail.com> 1578384538 +0900

Create local repository: .trs
```

## hash-object

```
#2020-01-10 11:52|fukudayu@NPC206:~/PythonProjects/wyag/right (master*?)
$ ../wyag hash-object -w ../libwyag.py
5a9c82bea9f4e40224d79b0032423172d9c6276e
```

## log

```
$ ../wyag log 18e03518a31e3ee2fbae3ae31250728bc84cf5f9
digraph wyaglog{
c_18e03518a31e3ee2fbae3ae31250728bc84cf5f9 -> c_effc0412e516104c144eb9517b57727481009ef6
c_effc0412e516104c144eb9517b57727481009ef6 -> c_df302de347d710e480f083fcdd223334354ecaf5
c_df302de347d710e480f083fcdd223334354ecaf5 -> c_ee3f83c18d5da918849efe98fb67a9a8e03b437c
c_ee3f83c18d5da918849efe98fb67a9a8e03b437c -> c_d6fcf3d68e13e593ee46e97c70296801ff480e33
c_d6fcf3d68e13e593ee46e97c70296801ff480e33 -> c_be76ddb827ed2bd1ece18992c25e3c7b4a964874
c_be76ddb827ed2bd1ece18992c25e3c7b4a964874 -> c_25e15f8e03ac2aa81c8fcd9fa0e72edffdc1f8a2
c_25e15f8e03ac2aa81c8fcd9fa0e72edffdc1f8a2 -> c_4e83dec2b6c78104c027b28aaba32281c31e1ac1
}
```

## ls-tree

```
$ ./wyag ls-tree d0e9e6c6394759defbedc11f4c28ad87b723c90e
040000 tree aaa96ced2d9a1c8e72c56b253a0e2fe78393feb7	hoge
```

## checkout

```
#2020-01-10 19:05|fukudayu@NPC206:~/PythonProjects/wyag (master*?)
$ ./wyag checkout 7c67dc35b3478a30849e8f62331eb8215194694a co
```

## compress <=> decompress

```
In [7]: result = b'commit' + b' ' + str(len(original_data)).encode() + b'\x00' + b'hello world'

In [8]: result
Out[8]: b'commit 21\x00hello world'

In [9]: compressed = zlib.compress(result)

In [10]: compressed
Out[10]: b'x\x9cK\xce\xcf\xcd\xcd,Q02d\xc8H\xcd\xc9\xc9W(\xcf/\xcaI\x01\x00O\xf3\x07i'

In [11]: raw = zlib.decompress(compressed)

In [12]: raw
Out[12]: b'commit 21\x00hello world'

In [13]: x = raw.find(b' ')

In [14]: x
Out[14]: 6
In [15]: fmt = raw[0:x]

In [16]: fmt
Out[16]: b'commit'

In [17]: y = raw.find(b'\x00', x)

In [18]: y
Out[18]: 9

In [19]: s = raw[x:y].decode("ascii")

In [20]: s
Out[20]: ' 21'

In [21]: size = int(s)

In [22]: size
Out[22]: 21
In [23]: bs = len(raw)-y-1

In [24]: bs
Out[24]: 11
```
