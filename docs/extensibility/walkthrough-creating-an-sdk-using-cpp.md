---
title: 'チュートリアル: C++ を使用して、SDK の作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33880dc3b9c359798c47c666debc3d5564524794
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>チュートリアル: C++ を使用して SDK を作成します。
このチュートリアルでは、ネイティブ C++ 数値演算ライブラリ、SDK パッケージとして、Visual Studio Extension (VSIX)、SDK を作成し、それを使用して、アプリを作成する方法を示します。 このチュートリアルは、次の手順に分かれています。  
  
-   [ネイティブおよび Windows ランタイム ライブラリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [NativeMathVSIX 拡張機能プロジェクトを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [クラス ライブラリを使用するサンプル アプリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)です。  
  
##  <a name="createClassLibrary"></a> ネイティブおよび Windows ランタイム ライブラリを作成するには  
  
1.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
2.  テンプレートの一覧で展開**Visual C**、 **Windows ユニバーサル**、クリックして、 **DLL (Windows ユニバーサル アプリ)**テンプレート。 **名前**ボックスで、指定`NativeMath`を選択し、 **OK**ボタンをクリックします。  
  
3.  次のコードに合わせて NativeMath.h を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  このコードに合わせて NativeMath.cpp を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、**ソリューション 'NativeMath'**を選択し**追加**、**新しいプロジェクト**です。  
  
6.  テンプレートの一覧で展開**Visual C**、クリックして、 **Windows ランタイム コンポーネント**テンプレート。 **名前**ボックスで、指定`NativeMathWRT`を選択し、 **OK**ボタンをクリックします。  
  
7.  このコードに合わせて class1.h の中を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  このコードに合わせて Class1.cpp を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. メニュー バーの **[ビルド]**、 **[ソリューションのビルド]**の順にクリックします。  
  
##  <a name="createVSIX"></a> NativeMathVSIX 拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、**ソリューション 'NativeMath'**を選択し**追加**、**新しいプロジェクト**です。  
  
2.  テンプレートの一覧で展開**Visual c#**、 **Extensibility**、し、 **VSIX プロジェクト**です。 **名前**ボックスで、指定**NativeMathVSIX**を選択し、 **OK**ボタンをクリックします。
  
3.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **source.extension.vsixmanifest**を選択し**コードの表示**です。  
  
4.  次の XML を使用すると、既存の XML を置換できます。  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **NativeMathVSIX**プロジェクトをクリックして**追加**、**新しい項目の**します。  
  
6.  一覧で**Visual c# アイテム**、展開**データ**、し、 **XML ファイル**です。 **名前**ボックスで、指定`SDKManifest.xml`を選択し、 **OK**ボタンをクリックします。  
  
7.  ファイルの内容を置き換えるには、この XML を使用します。  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. **ソリューション エクスプ ローラー**で、 **NativeMathVSIX**プロジェクトから、このフォルダー構造を作成します。  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
9. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、**ソリューション 'NativeMath'**を選択し**ファイル エクスプ ローラーでフォルダーを開く**です。  
  
10. **ファイル エクスプ ローラー**、$SolutionRoot$\NativeMath\NativeMath.h をコピーし、**ソリューション エクスプ ローラー**で、 **NativeMathVSIX**プロジェクトを貼り付けて、$SolutionRoot$ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\ フォルダーです。  
  
     $SolutionRoot$\Debug\NativeMath\NativeMath.lib をコピーし、$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\ フォルダーに貼り付けます。  
  
     $SolutionRoot$\Debug\NativeMath\NativeMath.dll をコピーし、$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\ フォルダーに貼り付けます。  
  
     $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll をコピーし、$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86 フォルダーに貼り付けます。  
  
     $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd をコピーし、$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral フォルダーに貼り付けます。  
  
     $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri をコピーし、$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral フォルダーに貼り付けます。  
  
11. $SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\ フォルダーで、NativeMathSDK.props、という名前のテキスト ファイルを作成し、これで、次の内容を貼り付けます。  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. メニュー バーで、次のように選択します。**ビュー**、**その他のウィンドウ**、**プロパティ ウィンドウ**(キーボード: F4 キーを押します)。  
  
13. **ソリューション エクスプ ローラー**、select、 **NativeMathWRT.winmd**ファイル。 **プロパティ**ウィンドウで、変更、**ビルド アクション**プロパティを**コンテンツ**、し、変更、 **VSIX に含める**プロパティ**True**です。  
  
     このプロセスを繰り返します、 **NativeMath.h**ファイル。  
  
     このプロセスを繰り返します、 **NativeMathWRT.pri**ファイル。  
  
     このプロセスを繰り返します、 **NativeMath.Lib**ファイル。  
  
     このプロセスを繰り返します、 **NativeMathSDK.props**ファイル。  
  
14. **ソリューション エクスプ ローラー**、select、 **NativeMath.h**ファイル。 **プロパティ**ウィンドウで、変更、 **VSIX に含める**プロパティを**True**です。  
  
     このプロセスを繰り返します、 **NativeMath.dll**ファイル。  
  
     このプロセスを繰り返します、 **NativeMathWRT.dll**ファイル。  
  
     このプロセスを繰り返します、 **SDKManifest.xml**ファイル。  
  
15. メニュー バーの **[ビルド]**、 **[ソリューションのビルド]**の順にクリックします。  
  
16. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **NativeMathVSIX**プロジェクトをクリックして**ファイル エクスプ ローラーでフォルダーを開く**です。  
  
17. **ファイル エクスプ ローラー**$SolutionRoot$ \NativeMathVSIX\bin\Debug\ フォルダーに移動、およびインストールを開始する NativeMathVSIX.vsix を実行します。  
  
18. 選択、**インストール**ボタンをクリックし、インストールが終了するまで待機し、Visual Studio を起動します。  
  
##  <a name="createSample"></a> クラス ライブラリを使用するサンプル アプリを作成するには  
  
1.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
2.  テンプレートの一覧で展開**Visual C**、 **Windows ユニバーサル**、し、 **Blank App**です。 **名前**ボックスで、指定**NativeMathSDKSample**を選択し、 **OK**ボタンをクリックします。  
  
3.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **NativeMathSDKSample**プロジェクトをクリックして**追加**、**参照**です。  
  
4.  **参照の追加**ダイアログ ボックスで、参照型の一覧で展開**ユニバーサル Windows**、し、**拡張**です。 最後に、選択、**ネイティブ Math SDK**チェック ボックスをオンにして、 **OK**ボタンをクリックします。
  
5.  NativeMathSDKSample のプロジェクトのプロパティを表示します。  
  
     NativeMathSDK.props で定義されているプロパティは、参照を追加したときに適用されました。 これを確認するには確認するには、 **vc++ ディレクトリ**のプロジェクトのプロパティ**構成プロパティ**です。  
  
6.  **ソリューション エクスプ ローラー**MainPage.xaml を開き、次の XAML を使用してその内容を置き換えます。  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7.  このコードに合わせて Mainpage.xaml.h を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. このコードに合わせて MainPage.xaml.cpp を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. アプリの実行に F5 キーを押します。  
  
10. アプリで、任意の 2 つの数値を入力し、操作を選択し、、 **=**ボタンをクリックします。  
  
     正しい結果が表示されます。  
  
 このチュートリアルで作成およびへの呼び出しを拡張機能 SDK を使用する方法を示しました、[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]ライブラリと以外[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]ライブラリです。  
  
## <a name="next-steps"></a>次の手順  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: c# または Visual Basic を使用して、SDK の作成](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [ソフトウェア開発キットを作成する](../extensibility/creating-a-software-development-kit.md)