---
title: 'チュートリアル: ClickOnce 配置 API で必要に応じてアセンブリをダウンロードする |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 6e1f9e1a2115e61e46e0050c1e6504e73c0180fe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199135"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>チュートリアル : ClickOnce 配置 API を使用して必要に応じてアセンブリをダウンロードする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

既定では、内のすべてのアセンブリに含まれる、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーションが、アプリケーションを初めて実行したときにダウンロードされます。 ただし、少数のユーザーによって使用される、アプリケーションの部分があります。 その場合は、そのような型を作成するときにだけアセンブリをダウンロードすることができます。 次のチュートリアルでは、"optional"として、アプリケーション内の特定のアセンブリをマークする方法と、クラスを使用してダウンロードする方法、<xref:System.Deployment.Application>共通言語ランタイム (CLR) がそれらを要求したときに、名前空間。  
  
> [!NOTE]
>  これを行うには、アプリケーションが完全な信頼で実行する必要があります。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するには、次のコンポーネントのいずれかが必要です。  
  
-   Windows SDK の。 Windows SDK は、Microsoft ダウンロード センターからダウンロードできます。  
  
-   Visual Studio  
  
## <a name="creating-the-projects"></a>プロジェクトの作成  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>オンデマンドでアセンブリを使用するプロジェクトを作成するには  
  
1.  任意のという名前のディレクトリを作成します。  
  
2.  Windows SDK コマンド プロンプトを開き、または[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]コマンド プロンプト。  
  
3.  任意のディレクトリに変更します。  
  
4.  次のコマンドを使用して公開/秘密キーのペアを生成します。  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  という名前のクラスを定義してメモ帳または別のテキスト エディターを使用して`DynamicClass`という名前の 1 つのプロパティを持つ`Message`します。  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6.  テキストをという名前のファイルとして保存`ClickOnceLibrary.cs`または`ClickOnceLibrary.vb`任意のディレクトリに、ユーザーが使用する言語によって異なります。  
  
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
  
9. エディター、テキストを使用して新しいファイルを作成し、次のコードを入力します。 このコードは、必要な場合に、ClickOnceLibrary アセンブリをダウンロードする Windows フォーム アプリケーションを作成します。  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. コードへの呼び出しを見つけます<xref:System.Reflection.Assembly.LoadFile%2A>します。  
  
11. 設定`PublicKeyToken`以前に取得した値にします。  
  
12. いずれかとして保存`Form1.cs`または`Form1.vb`します。  
  
13. 次のコマンドを使用して実行可能ファイルにコンパイルします。  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>アセンブリをオプションとしてマークする  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>MageUI.exe を使用して ClickOnce アプリケーションでは省略可能としてアセンブリをマークするには  
  
1.  」の説明に従って、アプリケーション マニフェストを作成、MageUI.exe を使用して[チュートリアル: ClickOnce アプリケーションを手動で配置](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。 アプリケーション マニフェストの次の設定を使用します。  
  
    -   アプリケーション マニフェストの名前を付けます`ClickOnceOnDemand`します。  
  
    -   **ファイル**ClickOnceLibrary.dll 行内設定 ページで、**ファイルの種類**列**None**します。  
  
    -   **ファイル**ClickOnceLibrary.dll 行、型のページで、`ClickOnceLibrary.dll`で、**グループ**列。  
  
2.  配置マニフェストの作成」の説明に従って、MageUI.exe を使用して[チュートリアル: ClickOnce アプリケーションを手動で配置](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。 配置マニフェストに、次の設定を使用します。  
  
    -   配置マニフェストの名前を付けます`ClickOnceOnDemand`します。  
  
## <a name="testing-the-new-assembly"></a>新しいアセンブリをテストする  
  
#### <a name="to-test-your-on-demand-assembly"></a>オンデマンド アセンブリをテストするには  
  
1.  アップロード、 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Web サーバーに配置します。  
  
2.  デプロイされるアプリケーションを起動[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]配置マニフェストへの URL を入力して、Web ブラウザーから。 呼び出す場合、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション`ClickOnceOnDemand`adatum.com のルート ディレクトリにアップロードして、URL は次のようになります。  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  メイン フォームが表示されたら、 <xref:System.Windows.Forms.Button>をクリックします。 文字列「こんにちは, World!」というメッセージ ボックス ウィンドウに表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Deployment.Application.ApplicationDeployment>



