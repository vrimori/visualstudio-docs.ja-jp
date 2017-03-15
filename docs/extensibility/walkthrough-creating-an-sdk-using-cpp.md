---
title: "チュートリアル: C++ を使用して SDK を作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 32
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d4458cb2cf0f3f198b2931beec15f8eead446ba6
ms.openlocfilehash: 3baf914755f0cdd4e0aa0a6c1405126faeec0364
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-an-sdk-using-c"></a>チュートリアル: C++ を使用して SDK を作成します。
このチュートリアルでは、ネイティブ C++ 数値演算ライブラリ、SDK パッケージとして、Visual Studio Extension (VSIX)、SDK を作成してから、アプリの作成に使用する方法を示します。 このチュートリアルは、次の手順に分かれています。  
  
-   [ネイティブと Windows ランタイム ライブラリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [NativeMathVSIX 拡張機能プロジェクトを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [クラス ライブラリを使用するサンプル アプリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
##  <a name="a-namecreateclasslibrarya-to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>ネイティブと Windows ランタイム ライブラリを作成するには  
  
1.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
2.  テンプレートの一覧で  **Visual C**、 **Windows ストア**、クリックして、 **DLL (Windows ストア アプリ)**テンプレートです。 **名**ボックスで、指定`NativeMath`を選択し、 **OK**  ボタンをクリックします。  
  
3.  次のコードに合わせて NativeMath.h を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCpp&#1;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  このコードのように NativeMath.cpp を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCpp&#2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き**ソリューション 'NativeMath'**、にして**追加**、**新しいプロジェクト**します。  
  
6.  テンプレートの一覧で  **Visual C**、クリックして、 **Windows ランタイム コンポーネント**テンプレートです。 **名**ボックスで、指定`NativeMathWRT`を選択し、 **OK**  ボタンをクリックします。  
  
7.  このコードのように class1.h の中を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCpp&#3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  このコードのように Class1.cpp を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCpp&4;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. メニュー バーの **[ビルド]**、 **[ソリューションのビルド]**の順にクリックします。  
  
##  <a name="a-namecreatevsixa-to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>NativeMathVSIX 拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き**ソリューション 'NativeMath'**、にして**追加**、**新しいプロジェクト**します。  
  
2.  テンプレートの一覧で  **Visual c#**、**拡張**、し、 **VSIX パッケージ**します。 **名**ボックスで、指定**NativeMathVSIX**を選択し、 **OK**  ボタンをクリックします。  
  
3.  VSIX マニフェスト デザイナーが表示されたら、それを閉じます。  
  
4.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き**source.extension.vsixmanifest**、にして**コードの表示**します。  
  
5.  次の XML を使用すると、既存の XML を置換できます。  
  
    [!code-xml[CreatingAnSDKUsingCpp&6;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

6.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **NativeMathVSIX**プロジェクトを開いて、**追加**、 **新しい項目の**です。  
  
7.  一覧で**Visual c# アイテム**、展開**データ**、し、 **XML ファイル**します。 **名**ボックスで、指定`SDKManifest.xml`を選択し、 **OK**  ボタンをクリックします。  
  
8.  ファイルの内容を置き換えるには、この XML を使用します。  
  
     [!code-xml[CreatingAnSDKUsingCpp&#5;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
9. **ソリューション エクスプ ローラー**で、 **NativeMathVSIX**プロジェクトから、このフォルダー構造を作成します。  
  
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
  
10. **ソリューション エクスプ ローラー**、ショートカット メニューを開き**ソリューション 'NativeMath'**、にして**ファイル エクスプ ローラーでフォルダーを開く**します。  
  
11. **ファイル エクスプ ローラー**、\NativeMath\NativeMath.h をコピーし、**ソリューション エクスプ ローラー**で、 **NativeMathVSIX**プロジェクト、\DesignTime\CommonConfiguration\Neutral\Include\ フォルダーに貼り付けます。  
  
     \Debug\NativeMath\NativeMath.lib をコピーし、\DesignTime\Debug\x86\ フォルダーに貼り付けます。  
  
     \Debug\NativeMath\NativeMath.dll をコピーして \Redist\Debug\x86\ フォルダーに貼り付けます。  
  
     DebugNativeMathWRTNativeMathWRT.dll をコピーして RedistDebugx86 フォルダーに貼り付けます。  
  
     DebugNativeMathWRTNativeMathWRT.winmd をコピーして ReferencesCommonConfigurationNeutral フォルダーに貼り付けます。  
  
     DebugNativeMathWRTNativeMathWRT.pri をコピーして ReferencesCommonConfigurationNeutral フォルダーに貼り付けます。  
  
12. \DesignTime\Debug\x86\ フォルダーに NativeMathSDK.props、というテキスト ファイルを作成しに次の内容を貼り付けます。  
  
    [!code-xml[CreatingAnSDKUsingCpp&#7;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. メニュー バー**ビュー**、**その他のウィンドウ**、**プロパティ ウィンドウ**(キーボード: F4 キーを押します)。  
  
14. **ソリューション エクスプ ローラー**を選択、 **NativeMathWRT.winmd**ファイルです。 **プロパティ**ウィンドウで、変更、**ビルド アクション**プロパティを**コンテンツ**、し、変更、 **VSIX に含める**プロパティを**True**します。  
  
     に対して、このプロセスを繰り返して、 **SimpleMath.pri**ファイルです。  
  
     に対して、このプロセスを繰り返して、 **NativeMath.Lib**ファイルです。  
  
     に対して、このプロセスを繰り返して、 **NativeMathSDK.props**ファイルです。  
  
15. **ソリューション エクスプ ローラー**を選択、 **NativeMath.h**ファイルです。 **プロパティ**ウィンドウで、変更、 **VSIX に含める**プロパティを**True**します。  
  
     に対して、このプロセスを繰り返して、 **NativeMath.dll**ファイルです。  
  
     に対して、このプロセスを繰り返して、 **NativeMathWRT.dll**ファイルです。  
  
     に対して、このプロセスを繰り返して、 **SDKManifest.xml**ファイルです。  
  
16. メニュー バーの **[ビルド]**、 **[ソリューションのビルド]**の順にクリックします。  
  
17. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **NativeMathVSIX**プロジェクトを開いて、**ファイル エクスプ ローラーでフォルダーを開く**します。  
  
18. **ファイル エクスプ ローラー**、\bin\Debug\ フォルダーに移動し、インストールを開始する NativeMathVSIX.vsix を実行します。  
  
19. 選択、**インストール**ボタンをクリックし、インストールを完了するまで待機し、Visual Studio を再起動します。  
  
##  <a name="a-namecreatesamplea-to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>クラス ライブラリを使用するサンプル アプリを作成するには  
  
1.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
2.  テンプレートの一覧で  **Visual C**、 **Windows ストア**、し、**空のアプリケーション**します。 **名**ボックスで、指定**NativeMathSDKSample**を選択し、 **OK**  ボタンをクリックします。  
  
3.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **NativeMathSDKSample**プロジェクトを開いて、**追加**、**参照**します。  
  
4.  **共通プロパティ**、 **Framework と参照**プロパティ] ページで、参照型の一覧で展開**Windows**、し、[**拡張**します。 詳細ウィンドウで [、**ネイティブ Math SDK**拡張機能を選択し、**新しい参照の追加**] ボタンをクリックします。  
  
5.  **参照の追加**ダイアログ ボックスで、**ネイティブ Math SDK**チェック ボックスをオンにして、 **OK**  ボタンをクリックします。  
  
6.  NativeMathSDKSample のプロジェクトのプロパティを表示します。  
  
     NativeMathSDK.props で定義されているプロパティは、参照を追加したときに適用されました。 これを確認するには確認するには、 **vc++ ディレクトリ**、プロジェクトのプロパティ**構成プロパティ**します。  
  
7.  **ソリューション エクスプ ローラー**MainPage.xaml を開き、次の XAML を使用してその内容を置き換えます。  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp&#1;](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
8.  このコードのように Mainpage.xaml.h を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp&#2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
9. このコードのように MainPage.xaml.cpp を更新します。  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp&#3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
10. アプリケーションを実行 F5 キーを押します。  
  
11. アプリケーションで、任意の&2; つの数値を入力し、操作を選択し、[、 ** = ** ] ボタンをクリックします。  
  
     正しい結果が表示されます。  
  
 このチュートリアルで作成およびへの呼び出しを拡張機能 SDK を使用する方法を示しました、[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]ライブラリと以外[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]ライブラリです。  
  
## <a name="next-steps"></a>次の手順  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: c# または Visual Basic を使用して SDK を作成します。](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [ソフトウェア開発キットを作成します。](../extensibility/creating-a-software-development-kit.md)
