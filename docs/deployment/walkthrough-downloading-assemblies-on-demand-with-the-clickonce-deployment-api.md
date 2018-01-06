---
title: "チュートリアル: ClickOnce 配置 API で必要に応じてアセンブリをダウンロードする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 640c0852a3745d11aae119e3c00e024b594d9132
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>チュートリアル : ClickOnce 配置 API を使用して必要に応じてアセンブリをダウンロードする
既定では、すべてのアセンブリに含める、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションの初回実行時にアプリケーションをダウンロードします。 ただし、少数のユーザーによって使用されているアプリケーションの部分があります。 その場合は、そのような型を作成するときにだけアセンブリをダウンロードすることができます。 次のチュートリアルでは、"optional"、として、アプリケーション内の特定のアセンブリをマークする方法と、クラスを使用してダウンロードする方法、<xref:System.Deployment.Application>共通言語ランタイム (CLR) を要求するときに名前空間。  
  
> [!NOTE]
>  これを行うには、アプリケーションが完全な信頼で実行する必要があります。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行する次のコンポーネントの 1 つ必要になります。  
  
-   Windows SDK。 Windows SDK は、Microsoft ダウンロード センターからダウンロードできます。  
  
-   Visual Studio  
  
## <a name="creating-the-projects"></a>プロジェクトの作成  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>オンデマンドでアセンブリを使用するプロジェクトを作成するには  
  
1.  任意のという名前のディレクトリを作成します。  
  
2.  Windows SDK コマンド プロンプトを開き、または[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コマンド プロンプトです。  
  
3.  任意のディレクトリに移動します。  
  
4.  次のコマンドを使用して公開/秘密キー ペアを生成します。  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  メモ帳または別のテキスト エディターを使用して、という名前のクラスを定義`DynamicClass`という名前の単一プロパティを持つ`Message`します。  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  テキストをという名前のファイルとして保存`ClickOnceLibrary.cs`または`ClickOnceLibrary.vb`任意のディレクトリに、使用する言語によって異なります。  
  
7.  ファイルをアセンブリにコンパイルします。  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  アセンブリの公開キー トークンを取得するには、次のコマンドを使用します。  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. エディター、テキストを使用して新しいファイルを作成し、次のコードを入力します。 このコードでは、必要な場合に、ClickOnceLibrary アセンブリをダウンロードする Windows フォーム アプリケーションを作成します。  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. コードへの呼び出しを見つける<xref:System.Reflection.Assembly.LoadFile%2A>です。  
  
11. 設定`PublicKeyToken`以前に取得した値にします。  
  
12. いずれかとして保存`Form1.cs`または`Form1.vb`です。  
  
13. 次のコマンドを使用して実行可能ファイルにコンパイルします。  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>アセンブリをオプションとしてマークする  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>MageUI.exe を使用して ClickOnce アプリケーションでは省略可能としてアセンブリをマークするには  
  
1.  」の説明に従って、アプリケーション マニフェストを作成、MageUI.exe を使用して[チュートリアル: ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)です。 アプリケーション マニフェストの次の設定を使用します。  
  
    -   アプリケーション マニフェストの名前を付けます`ClickOnceOnDemand`です。  
  
    -   **ファイル** ページで、ClickOnceLibrary.dll 行で、設定、**ファイルの種類**列を**なし**です。  
  
    -   **ファイル**ClickOnceLibrary.dll 行で、型のページ`ClickOnceLibrary.dll`で、**グループ**列です。  
  
2.  説明に従って、配置マニフェストを作成、MageUI.exe を使用して[チュートリアル: ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)です。 配置マニフェストに、次の設定を使用します。  
  
    -   配置マニフェストの名前を付けます`ClickOnceOnDemand`です。  
  
## <a name="testing-the-new-assembly"></a>新しいアセンブリをテストする  
  
#### <a name="to-test-your-on-demand-assembly"></a>オンデマンド アセンブリをテストするには  
  
1.  アップロード、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Web サーバーに配置します。  
  
2.  展開されているアプリケーションを起動[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェストへの URL を入力して、Web ブラウザーからです。 呼び出す場合は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション`ClickOnceOnDemand`adatum.com のルート ディレクトリにアップロードして、URL は次のようになります。  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  メイン フォームが表示されたら、 <xref:System.Windows.Forms.Button>をクリックします。 「こんにちは, World!」というメッセージ ボックス ウィンドウに文字列が表示されます。  
  
## <a name="see-also"></a>参照  
 <xref:System.Deployment.Application.ApplicationDeployment>