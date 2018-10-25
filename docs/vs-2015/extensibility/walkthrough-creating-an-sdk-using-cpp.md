---
title: 'チュートリアル: C++ を使用して、SDK の作成 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c10611ee05178f907c36aae268b0d6990a9e6606
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905702"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>チュートリアル: C++ を使用して SDK を作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルでは、ネイティブ C++ 数値演算ライブラリを SDK パッケージとして、Visual Studio Extension (VSIX)、SDK を作成し、それを使用して、アプリを作成する方法を示します。 このチュートリアルは、次の手順に分かれています。  
  
-   [ネイティブと Windows ランタイム ライブラリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [NativeMathVSIX 拡張機能プロジェクトを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [クラス ライブラリを使用するサンプル アプリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
##  <a name="createClassLibrary"></a> ネイティブと Windows ランタイム ライブラリを作成するには  
  
1.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]** の順にクリックします。  
  
2.  テンプレートの一覧で展開**Visual C**、 **Windows ストア**、クリックして、 **DLL (Windows ストア アプリ)** テンプレート。 **名前**ボックスで、指定`NativeMath`、選択し、 **OK**ボタン。  
  
3.  次のコードに合わせて NativeMath.h を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4.  このコードに合わせて NativeMath.cpp を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き**ソリューション 'NativeMath'** を選び、**追加**、**新しいプロジェクト**します。  
  
6.  テンプレートの一覧で展開**Visual C**、クリックして、 **Windows ランタイム コンポーネント**テンプレート。 **名前**ボックスで、指定`NativeMathWRT`、選択し、 **OK**ボタン。  
  
7.  このコードに合わせて class1.h の中を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8.  このコードに合わせて Class1.cpp を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. メニュー バーの **[ビルド]**、 **[ソリューションのビルド]** の順にクリックします。  
  
##  <a name="createVSIX"></a> NativeMathVSIX 拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き**ソリューション 'NativeMath'** を選び、**追加**、**新しいプロジェクト**します。  
  
2.  テンプレートの一覧で  **Visual c#**、**拡張**、し、 **VSIX パッケージ**します。 **名前**ボックスで、指定**NativeMathVSIX**、選択し、 **OK**ボタン。  
  
3.  VSIX マニフェスト デザイナーが表示されたら、それを閉じます。  
  
4.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き**source.extension.vsixmanifest**を選び、**コードの表示**します。  
  
5.  次の XML を使用すると、既存の XML を置換できます。  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **NativeMathVSIX**プロジェクトを選び、**追加**、**新しい項目の**します。  
  
7.  一覧で**Visual c# アイテム**、展開**データ**、し、 **XML ファイル**します。 **名前**ボックスで、指定`SDKManifest.xml`、選択し、 **OK**ボタン。  
  
8.  ファイルの内容を置き換えるには、この XML を使用します。  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. **ソリューション エクスプ ローラー**の**NativeMathVSIX**プロジェクトで、このフォルダー構造を作成します。  
  
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
  
10. **ソリューション エクスプ ローラー**、ショートカット メニューを開き**ソリューション 'NativeMath'** を選び、**ファイル エクスプ ローラーでフォルダーを開く**します。  
  
11. **ファイル エクスプ ローラー**、\NativeMath\NativeMath.h をコピーし、**ソリューション エクスプ ローラー**の**NativeMathVSIX**プロジェクトで、\DesignTime\ に貼り付けるCommonConfiguration\Neutral\Include\ フォルダーです。  
  
     \Debug\NativeMath\NativeMath.lib のコピーし、\DesignTime\Debug\x86\ フォルダーに貼り付けます。  
  
     \Debug\NativeMath\NativeMath.dll をコピーし、\Redist\Debug\x86\ フォルダーに貼り付けます。  
  
     DebugNativeMathWRTNativeMathWRT.dll をコピーし、RedistDebugx86 フォルダーに貼り付けます。  
  
     DebugNativeMathWRTNativeMathWRT.winmd をコピーし、ReferencesCommonConfigurationNeutral フォルダーに貼り付けます。  
  
     DebugNativeMathWRTNativeMathWRT.pri をコピーし、ReferencesCommonConfigurationNeutral フォルダーに貼り付けます。  
  
12. \DesignTime\Debug\x86\ フォルダーで NativeMathSDK.props、というテキスト ファイルを作成し、これで、次の内容を貼り付けます。  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. メニュー バーで、**ビュー**、**その他の Windows**、**プロパティ ウィンドウ**(キーボード: F4 キーを押します)。  
  
14. **ソリューション エクスプ ローラー**を選択、 **NativeMathWRT.winmd**ファイル。 **プロパティ**ウィンドウで、変更、**ビルド アクション**プロパティを**コンテンツ**、し、変更、 **VSIX に含める**プロパティ**True**します。  
  
     この手順を繰り返します、 **SimpleMath.pri**ファイル。  
  
     この手順を繰り返します、 **NativeMath.Lib**ファイル。  
  
     この手順を繰り返します、 **NativeMathSDK.props**ファイル。  
  
15. **ソリューション エクスプ ローラー**を選択、 **NativeMath.h**ファイル。 **プロパティ**ウィンドウで、変更、 **VSIX に含める**プロパティを**True**します。  
  
     この手順を繰り返します、 **NativeMath.dll**ファイル。  
  
     この手順を繰り返します、 **NativeMathWRT.dll**ファイル。  
  
     この手順を繰り返します、 **SDKManifest.xml**ファイル。  
  
16. メニュー バーの **[ビルド]**、 **[ソリューションのビルド]** の順にクリックします。  
  
17. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **NativeMathVSIX**プロジェクトを選び、**ファイル エクスプ ローラーでフォルダーを開く**します。  
  
18. **ファイル エクスプ ローラー**\bin\Debug\ フォルダーに移動して、インストールを開始する NativeMathVSIX.vsix を実行します。  
  
19. 選択、**インストール**ボタンをクリックし、インストールを完了するまで待機し、Visual Studio を再起動します。  
  
##  <a name="createSample"></a> クラス ライブラリを使用するサンプル アプリを作成するには  
  
1. メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]** の順にクリックします。  
  
2. テンプレートの一覧で  **Visual C**、 **Windows ストア**、し、**空のアプリ**します。 **名前**ボックスで、指定**NativeMathSDKSample**、選択し、 **OK**ボタン。  
  
3. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **NativeMathSDKSample**プロジェクトを選び、**追加**、**参照**します。  
  
4. **共通プロパティ**、 **Framework と参照**プロパティ ページで、参照型の一覧で、展開**Windows**、し、**拡張機能**. 詳細] ウィンドウで、[、**ネイティブ Math SDK**拡張機能を選択し、**新しい参照の追加**ボタンをクリックします。  
  
5. **参照の追加**ダイアログ ボックスで、**ネイティブ Math SDK**チェック ボックスをオンにして、 **OK**ボタン。  
  
6. NativeMathSDKSample のプロジェクトのプロパティを表示します。  
  
    NativeMathSDK.props で定義したプロパティは、参照を追加したときに適用されました。 これを調べることで確認できます、 **vc++ ディレクトリ**、プロジェクトのプロパティ**構成プロパティ**します。  
  
7. **ソリューション エクスプ ローラー**MainPage.xaml を開き、次の XAML を使用してそのコンテンツを置き換えます。  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. このコードに合わせて Mainpage.xaml.h を更新します。  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. このコードに合わせて MainPage.xaml.cpp を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. アプリを実行する、F5 キーを選択します。  
  
11. アプリでは、任意の 2 つの数値を入力し、操作を選択し、、 **=** ボタンをクリックします。  
  
     正しい結果が表示されます。  
  
    このチュートリアルで作成して呼び出すために、拡張機能 SDK を使用、する方法を示しました、[!INCLUDE[wrt](../includes/wrt-md.md)]ライブラリと以外[!INCLUDE[wrt](../includes/wrt-md.md)]ライブラリ。  
  
## <a name="next-steps"></a>次の手順  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: c# または Visual Basic を使用して、SDK の作成](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [ソフトウェア開発キットを作成する](../extensibility/creating-a-software-development-kit.md)

