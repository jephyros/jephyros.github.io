

### 1. 사전 준비
* **npx expo prebuild**: 프로젝트에 `ios` 폴더가 있어야 합니다. (없다면 터미널에서 실행)
* **Certificates & Profiles**: Apple Developer Program에 등록된 계정이 필요하며, Xcode의 `Signing & Capabilities` 설정에서 개발자 팀(Team)이 선택되어 있어야 합니다.

---

### 2. Xcode에서 .ipa 파일 생성 단계

#### Step 1: 빌드 타겟 설정
1. Xcode 상단 툴바에서 프로젝트 이름 옆에 있는 기기 선택 영역을 클릭합니다.
2. 실행 기기(Simulator 등) 대신 **Any iOS Device (arm64)**를 선택합니다. (실제 기기를 연결한 상태에서 선택해도 됩니다.)

#### Step 2: 아카이브(Archive) 실행
1. Xcode 상단 메뉴에서 **Product > Archive**를 클릭합니다.
2. 빌드가 시작되며, 프로젝트 크기에 따라 몇 분 정도 소요됩니다.

#### Step 3: 배포 마법사 실행
1. 빌드가 완료되면 **Organizer** 창이 자동으로 뜹니다. (안 뜨면 메뉴의 `Window > Organizer` 선택)
2. 목록에서 방금 만든 아카이브를 선택하고 오른쪽의 **Distribute App** 버튼을 누릅니다.

#### Step 4: 배포 방식 선택
1. **Custom** 또는 **App Store Connect** 중 상황에 맞는 옵션을 선택합니다. 
   * TestFlight나 앱스토어 업로드가 목적이면 **App Store Connect**를 선택합니다.
   * 단순히 파일만 추출하고 싶다면 **Ad Hoc** 또는 **Enterprise**(해당하는 경우)를 선택합니다.
2. 'Export' 또는 'Upload' 단계에서 **Export**를 선택하면 파일을 저장할 위치를 묻는 창이 나옵니다.

#### Step 5: 파일 저장
1. 모든 설정을 마치고 **Export**를 클릭하면 폴더가 하나 생성됩니다.
2. 그 폴더 안에 우리가 찾는 **`ProjectName.ipa`** 파일이 들어 있습니다.

---

### 3. 요약 및 팁
* **장점**: EAS 서버 대기 시간 없이 본인 맥북의 성능으로 빠르게 빌드할 수 있고, 클라우드 빌드 횟수 제한을 쓰지 않습니다.
* **주의**: Xcode에서 수동으로 빌드할 때는 `App.json`이나 `Expo Config`의 설정(버전 번호 등)이 `Info.plist`에 제대로 반영되었는지 확인해야 합니다. 보통 `prebuild`를 다시 실행하면 자동으로 동기화됩니다.

이제 추출된 `.ipa` 파일을 직접 TestFlight에 올리거나, 배포용으로 활용하시면 됩니다!
