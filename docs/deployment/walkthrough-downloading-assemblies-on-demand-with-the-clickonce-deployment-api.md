---
title: 'チュートリアル: ClickOnce 配置 API で必要に応じてアセンブリをダウンロード |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c45f600462d1862b9f50e12c5849d9d7175310a4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989216"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>チュートリアル: ClickOnce 配置 API で必要に応じてアセンブリをダウンロードします。
既定では、内のすべてのアセンブリに含まれる、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションが、アプリケーションを初めて実行したときにダウンロードされます。 ただし、少数のユーザーによって使用される、アプリケーションの部分があります。 その場合は、そのような型を作成するときにだけアセンブリをダウンロードすることができます。 以下のチュートリアルでは、アプリケーション内の特定のアセンブリに "オプション" マークを付ける方法、および共通言語ランタイム (CLR) でそのアセンブリが必要なときに <xref:System.Deployment.Application> 名前空間にあるクラスを使用してアセンブリをダウンロードする方法について説明します。  
  
> [!NOTE]
>  これを行うには、アプリケーションが完全な信頼で実行する必要があります。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するには、次のコンポーネントのいずれかが必要です。  
  
-   Windows SDK の。 Windows SDK は、Microsoft ダウンロード センターからダウンロードできます。  
  
-   Visual Studio  
  
## <a name="create-the-projects"></a>プロジェクトを作成します。  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>オンデマンドでアセンブリを使用するプロジェクトを作成するには  
  
1. 任意のという名前のディレクトリを作成します。  
  
2. Windows SDK コマンド プロンプトを開き、または[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コマンド プロンプト。  
  
3. 任意のディレクトリに変更します。  
  
4. 次のコマンドを使用して公開/秘密キーのペアを生成します。  
  
   ```cmd  
   sn -k TestKey.snk  
   ```  
  
5. という名前のクラスを定義してメモ帳または別のテキスト エディターを使用して`DynamicClass`という名前の 1 つのプロパティを持つ`Message`します。  
  
    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6. テキストをという名前のファイルとして保存*ClickOnceLibrary.cs*または*ClickOnceLibrary.vb*、使用する、言語に応じて、*任意*ディレクトリ。  
  
7. ファイルをアセンブリにコンパイルします。  
  
   ```csharp  
   csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
   ```  
  
   ```vb  
   vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
   ```  
  
8. アセンブリの公開キー トークンを取得するには、次のコマンドを使用します。  
  
   ```cmd  
   sn -T ClickOnceLibrary.dll  
   ```  
  
9. エディター、テキストを使用して新しいファイルを作成し、次のコードを入力します。 このコードは、必要な場合に、ClickOnceLibrary アセンブリをダウンロードする Windows フォーム アプリケーションを作成します。  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. コードへの呼び出しを見つけます<xref:System.Reflection.Assembly.LoadFile%2A>します。  
  
11. 設定`PublicKeyToken`以前に取得した値にします。  
  
12. いずれかとして保存*Form1.cs*または*Form1.vb*します。  
  
13. 次のコマンドを使用して実行可能ファイルにコンパイルします。  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="mark-assemblies-as-optional"></a>アセンブリをオプションとしてマーク  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>MageUI.exe を使用して ClickOnce アプリケーションでは省略可能としてアセンブリをマークするには  
  
1.  使用して*MageUI.exe*、」の説明に従って、アプリケーション マニフェストを作成[チュートリアル。ClickOnce アプリケーションを手動で展開](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。 アプリケーション マニフェストの次の設定を使用します。  
  
    -   アプリケーション マニフェストの名前を付けます`ClickOnceOnDemand`します。  
  
    -   **ファイル**] ページの [、 *ClickOnceLibrary.dll*行で、設定、**ファイルの種類**列**None**します。  
  
    -   **ファイル**ページで、 *ClickOnceLibrary.dll*行に「`ClickOnceLibrary.dll`で、**グループ**列。  
  
2.  使用して*MageUI.exe*、配置マニフェストの作成」の説明に従って[チュートリアル。ClickOnce アプリケーションを手動で展開](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。 配置マニフェストに、次の設定を使用します。  
  
    -   配置マニフェストの名前を付けます`ClickOnceOnDemand`します。  
  
## <a name="testing-the-new-assembly"></a>新しいアセンブリをテストする  
  
#### <a name="to-test-your-on-demand-assembly"></a>オンデマンド アセンブリをテストするには  
  
1. アップロード、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Web サーバーに配置します。  
  
2. デプロイされるアプリケーションを起動[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェストへの URL を入力して、Web ブラウザーから。 呼び出す場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション`ClickOnceOnDemand`adatum.com のルート ディレクトリにアップロードして、URL は次のようになります。  
  
   ```  
   http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
   ```  
  
3. メイン フォームが表示されたら、 <xref:System.Windows.Forms.Button>をクリックします。 メッセージ ボックス ウィンドウに "Hello, World!" という文字列が表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Deployment.Application.ApplicationDeployment>