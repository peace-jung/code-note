## Xcode 완전 삭제 하는 방법

- /Applications/Xcode.app
- /Library/Preferences/com.apple.dt.Xcode.plist
- ~/Library/Preferences/com.apple.dt.Xcode.plist
- ~/Library/Caches/com.apple.dt.Xcode
- ~/Library/Application Support/Xcode
- ~/Library/Developer
- ~/Library/Developer/Xcode
- ~/Library/Developer/CoreSimulator

script
```
rm -rf /Applications/Xcode.app /Library/Preferences/com.apple.dt.Xcode.plist ~/Library/Preferences/com.apple.dt.Xcode.plist ~/Library/Caches/com.apple.dt.Xcode ~/Library/Application Support/Xcode ~/Library/Developer ~/Library/Developer/Xcode ~/Library/Developer/CoreSimulator
```

## Xcode 용량 줄이는 방법
~/Library/Developer/Xcode/DerivedData 지우기
찾아보니 이 디렉토리에 프로젝트 별로 빌드에 관한 정보가 다 저장되어 있다고 한다. 그래서 프로젝트 인덱싱이 잘 안되면 이 디렉토리를 지우는 것이 좋다는 팁도 있는데, 이게 계속 쌓이기만 하고 있는 것이 문제인 것 같다. 이 디렉토리를 지우고 다시 빌드를 하면 다시 생기니 여러 프로젝트를 하는 경우에 이 디렉토리를 지워도 되는 것 같다.

~/Library/Developer/Xcode/Archives 지우기
찾은 김에 Xcode 디렉토리들을 하나씩 봤는데, Archives 디렉토리도 있었다. 이건 릴리즈한 것에 대해서 디버깅을 할 수 있는 정보들이 있었다. 이것도 Xcode 에서 archive 할때마다 쌓이는 모양이다. 이 디렉토리는 지워서 8GB를 얻었다.

~/Library/Developer/Xcode/iOS Device Logs 지우기
로그를 볼일이 없어서 지웠다.

~/Library/Developer/Xcode/iOS DeviceSupport 필요 없는 시뮬레이터 지우기

## Reference
https://devmjun.github.io/archive/Reduce-StorageInMac
