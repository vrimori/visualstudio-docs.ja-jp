---
title: 'チュートリアル: C++ を使用して、SDK の作成 |Microsoft Docs'
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
ms.openlocfilehash: 6311526df299da860c829520a2087ecc8d786600
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930645"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>チュートリアル: C++ を使用して SDK を作成します。
このチュートリアルでは、ネイティブ C++ 数値演算ライブラリを SDK パッケージとして、Visual Studio Extension (VSIX)、SDK を作成し、それを使用して、アプリを作成する方法を示します。 このチュートリアルは、次の手順に分かれています。  
  
-   [ネイティブと Windows ランタイム ライブラリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [NativeMathVSIX 拡張機能プロジェクトを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [クラス ライブラリを使用するサンプル アプリを作成するには](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
##  <a name="createClassLibrary"></a> ネイティブと Windows ランタイム ライブラリを作成するには  
  
1.  メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。  
  
2.  テンプレートの一覧で  **Visual C** > **Windows ユニバーサル**を選び、 **DLL (Windows ユニバーサル アプリ)** テンプレート。 **名前**ボックスで、指定`NativeMath`、選択し、 **OK**ボタン。  
  
3.  Update *NativeMath.h*次のコードに一致するようにします。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Update *NativeMath.cpp*このコードのようにします。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き**ソリューション 'NativeMath'** を選び、**追加** > **新しいプロジェクト**.  
  
6.  テンプレートの一覧で展開**Visual C**、クリックして、 **Windows ランタイム コンポーネント**テンプレート。 **名前**ボックスで、指定`NativeMathWRT`、選択し、 **OK**ボタン。  
  
7.  Update *Class1.h*このコードのようにします。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Update *Class1.cpp*このコードのようにします。  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. メニュー バーで、**[ビルド]** > **[ソリューションのビルド]** の順にクリックします。  
  
##  <a name="createVSIX"></a> NativeMathVSIX 拡張機能プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き**ソリューション 'NativeMath'** を選び、**追加** > **新しいプロジェクト**.  
  
2.  テンプレートの一覧で  **Visual c#** > **拡張**、し、 **VSIX プロジェクト**します。 **名前**ボックスで、指定**NativeMathVSIX**、選択し、 **OK**ボタン。
  
3.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き**source.extension.vsixmanifest**を選び、**コードの表示**します。  
  
4.  次の XML を使用すると、既存の XML を置換できます。  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **NativeMathVSIX**プロジェクトを選び、**追加** > **新しい項目の**.  
  
6.  一覧で**Visual c# アイテム**、展開**データ**、し、 **XML ファイル**します。 **名前**ボックスで、指定`SDKManifest.xml`、選択し、 **OK**ボタン。  
  
7.  ファイルの内容を置き換えるには、この XML を使用します。  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. **ソリューション エクスプ ローラー**、 **NativeMathVSIX**プロジェクトで、このフォルダー構造を作成します。  
  
    ```xml  
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
  
9. **ソリューション エクスプ ローラー**、ショートカット メニューを開き**ソリューション 'NativeMath'** を選び、**ファイル エクスプ ローラーでフォルダーを開く**します。  
  
10. **ファイル エクスプ ローラー**、コピー *$SolutionRoot$\NativeMath\NativeMath.h*、し、**ソリューション エクスプ ローラー**下で、 **NativeMathVSIX**プロジェクトで貼り付けることで、 *$SolutionRoot$ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\\* フォルダー。  
  
     コピー *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*に貼り付けると、 *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\* フォルダー。  
  
     コピー *$SolutionRoot$\Debug\NativeMath\NativeMath.dll*貼り付けます、 *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\\* フォルダー。  
  
     コピー *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll*貼り付けます、 *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86*フォルダー。  
     コピー *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd*貼り付けます、 *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral*フォルダー。  
  
     コピー *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri*貼り付けます、 *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral*フォルダー。  
  
11. *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\* フォルダー、という名前のテキスト ファイルを作成する*NativeMathSDK.props*、し、これで、次の内容を貼り付けます。  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. メニュー バーで、**ビュー** > **その他の Windows** > **プロパティ ウィンドウ**(キーボード: 選択、 **F4**キー)。  
  
13. **ソリューション エクスプ ローラー**を選択、 **NativeMathWRT.winmd**ファイル。 **プロパティ**ウィンドウで、変更、**ビルド アクション**プロパティを**コンテンツ**、し、変更、 **VSIX に含める**プロパティ**True**します。  
  
     この手順を繰り返します、 **NativeMath.h**ファイル。  
  
     この手順を繰り返します、 **NativeMathWRT.pri**ファイル。  
  
     この手順を繰り返します、 **NativeMath.Lib**ファイル。  
  
     この手順を繰り返します、 **NativeMathSDK.props**ファイル。  
  
14. **ソリューション エクスプ ローラー**を選択、 **NativeMath.h**ファイル。 **プロパティ**ウィンドウで、変更、 **VSIX に含める**プロパティを**True**します。  
  
     この手順を繰り返します、 **NativeMath.dll**ファイル。  
  
     この手順を繰り返します、 **NativeMathWRT.dll**ファイル。  
  
     この手順を繰り返します、 **SDKManifest.xml**ファイル。  
  
15. メニュー バーで、**[ビルド]** > **[ソリューションのビルド]** の順にクリックします。  
  
16. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **NativeMathVSIX**プロジェクトを選び、**ファイル エクスプ ローラーでフォルダーを開く**します。  
  
17. **ファイル エクスプ ローラー**に移動し、 *$SolutionRoot$ \NativeMathVSIX\bin\Debug*フォルダー、および実行します*NativeMathVSIX.vsix*インストールを開始します。  
  
18. 選択、**インストール**ボタンをクリックし、インストールを完了するまで待機し、Visual Studio を起動します。  
  
##  <a name="createSample"></a> クラス ライブラリを使用するサンプル アプリを作成するには  
  
1. メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。  
  
2. テンプレートの一覧で  **Visual C** > **Windows ユニバーサル**選び**空のアプリ**。 **名前**ボックスで、指定**NativeMathSDKSample**、選択し、 **OK**ボタン。  
  
3. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **NativeMathSDKSample**プロジェクトを選び、**追加** > **の参照**.  
  
4. **参照の追加**ダイアログ ボックスで、参照型の一覧で、展開**ユニバーサル Windows**、し、**拡張**します。 最後に、選択、**ネイティブ Math SDK**チェック ボックスをオンにして、 **OK**ボタンをクリックします。
  
5. NativeMathSDKSample のプロジェクトのプロパティを表示します。  
  
    プロパティで定義されている*NativeMathSDK.props*参照を追加したときに適用しました。 プロパティを調べることによって適用されたことを確認できる、 **vc++ ディレクトリ**、プロジェクトのプロパティ**構成プロパティ**します。  
  
6. **ソリューション エクスプ ローラー**オープン**MainPage.xaml**、し、次の XAML を使用して、そのコンテンツを置き換えます。  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7. Update *Mainpage.xaml.h*このコードのようにします。  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. Update *MainPage.xaml.cpp*このコードのようにします。  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. 選択、 **F5**キーをアプリを実行します。  
  
10. アプリでは、任意の 2 つの数値を入力し、操作を選択し、、 **=** ボタンをクリックします。  
  
     正しい結果が表示されます。  
  
    このチュートリアルで作成して呼び出すために、拡張機能 SDK を使用、する方法を示しました、[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]ライブラリと以外[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]ライブラリ。  
  
## <a name="next-steps"></a>次の手順  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: c# または Visual Basic を使用して SDK を作成します。](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [ソフトウェア開発キットを作成します。](../extensibility/creating-a-software-development-kit.md)
