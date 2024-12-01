iOSアプリをSwiftUIで開発し、アプリ内でMapboxの地図を使用するための基本的な導入手順をご紹介します。

## 1. Mapboxアカウントの作成とアクセストークンの取得

Mapboxのサービスを利用するには、アクセストークンが必要です。

- [Mapboxの公式サイト](https://www.mapbox.com/)でアカウントを作成します。
- ログイン後、アカウントページの「Access Tokens」セクションでデフォルトのパブリックトークンを確認できます。
- 必要に応じて、新しいトークンを作成し、適切なスコープ（例：`styles:read`、`styles:tiles`）を設定します。 

## 2. XcodeプロジェクトへのMapbox SDKの導入

Mapbox Maps SDK for iOSをプロジェクトに追加する方法はいくつかありますが、ここではSwift Package Managerを使用する手順を説明します。

- Xcodeでプロジェクトを開き、メニューバーから **File > Add Packages...** を選択します。
- 検索バーに以下のURLを入力します：`https://github.com/mapbox/mapbox-maps-ios.git`
- 表示されるバージョン選択画面で、適切なバージョンを選択し、プロジェクトのターゲットを指定して「Add Package」をクリックします。

## 3. アクセストークンのプロジェクトへの設定

取得したアクセストークンをプロジェクト内で使用できるように設定します。

- プロジェクトの `Info.plist` ファイルを開き、新しいキー `MBXAccessToken` を追加し、値として取得したアクセストークンを設定します。 

## 4. SwiftUIでのMapbox地図の表示

SwiftUIでMapboxの地図を表示するには、`UIViewRepresentable` を使用して UIKit の `MapView` をラップする必要があります。

以下はその実装例です：

```swift
import SwiftUI
import MapboxMaps

struct MapboxView: UIViewRepresentable {
    func makeUIView(context: Context) -> MapView {
        // アクセストークンの取得
        let accessToken = Bundle.main.object(forInfoDictionaryKey: "MBXAccessToken") as? String ?? ""
        // リソースオプションの設定
        let resourceOptions = ResourceOptions(accessToken: accessToken)
        // マップの初期設定
        let mapInitOptions = MapInitOptions(resourceOptions: resourceOptions)
        // MapViewの作成
        let mapView = MapView(frame: .zero, mapInitOptions: mapInitOptions)
        return mapView
    }

    func updateUIView(_ uiView: MapView, context: Context) {
        // 必要に応じてMapViewを更新
    }
}
```

この `MapboxView` をSwiftUIのビュー階層内で使用することで、地図を表示できます。

```swift
struct ContentView: View {
    var body: some View {
        MapboxView()
            .edgesIgnoringSafeArea(.all) // 必要に応じて地図を全画面表示
    }
}
```

## 参考文献

- 
- 
- 

これらの手順に従うことで、SwiftUIを使用したiOSアプリ内でMapboxの地図を表示する基本的な設定が完了します。 
