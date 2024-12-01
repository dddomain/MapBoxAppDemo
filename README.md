### iOSアプリにMapboxを導入する手順

![screenshot]()

---

#### 1. Mapboxアカウントの作成とトークンの設定

1. [Mapboxアカウントページ](https://account.mapbox.com)でアカウントを作成またはログインする。
2. ログイン後、提供されるデフォルトのパブリックアクセストークンを取得する。
3. Xcodeで`Info.plist`を開き、`MBXAccessToken`というキーを追加し、値として取得したトークンを設定する。

---

#### 2. Mapbox Maps SDKのインストール

##### Swift Package Managerを使用する場合:

1. Xcodeでプロジェクトを開き、`File` > `Add Packages...`を選択。
2. 検索バーに`https://github.com/mapbox/mapbox-maps-ios.git`を入力。
3. "Dependency Rule"として"Up to Next Major Version"を選択し、最小バージョンを`11.0.0`に設定。
4. `Add Package`をクリックし、`MapboxMaps`を選択して追加。
5. プロジェクトのターゲット設定で`Frameworks, Libraries, and Embedded Content`に`MapboxMaps`を追加。

---

#### 3. マップの表示

以下はSwiftUIを使った例:

```swift
import SwiftUI
import MapboxMaps

struct ContentView: View {
    var body: some View {
        let center = CLLocationCoordinate2D(latitude: 39.5, longitude: -98.0)
        Map(initialViewport: .camera(center: center, zoom: 2, bearing: 0, pitch: 0))
            .ignoresSafeArea()
    }
}
```

指定した座標を中心にマップを表示する。これで基本的なマップの表示ができる。

---

詳細や他のインストール方法は[Mapbox公式ドキュメント](https://docs.mapbox.com/ios/maps/guides/install/)を参照。
