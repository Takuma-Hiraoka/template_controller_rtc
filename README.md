# template_controller_rtc

RTCのテンプレート

## 使用方法
```bash
# 新しいgitのrepositoryを作っておく
mkdir [新しいrepository名]
cd [新しいrepository名]
git init
git remote add origin [新しく作ったrepositoryのurl]
git remote add template https://github.com/Takuma-Hiraoka/template_controller_rtc
git fetch --all
git checkout template/master
git checkout -b master
git push -u origin master
```

## Rename
auto_stabilizerという名前にする場合
```bash
./rename.sh auto_stabilizer
```
