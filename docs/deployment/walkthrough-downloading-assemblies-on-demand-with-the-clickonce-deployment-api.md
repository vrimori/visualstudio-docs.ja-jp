---
title: "チュートリアル : ClickOnce 配置 API を使用して必要に応じてアセンブリをダウンロードする | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "アセンブリ, ダウンロード [ClickOnce]"
  - "ClickOnce 配置, オンデマンド ダウンロード"
  - "オンデマンド アセンブリ, ClickOnce"
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# チュートリアル : ClickOnce 配置 API を使用して必要に応じてアセンブリをダウンロードする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

既定では、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの最初の実行時に、そのアプリケーションに含まれるすべてのアセンブリがダウンロードされます。  一方、アプリケーションには、一部のユーザーだけが使用する機能が含まれている場合があります。  この場合は、そのような機能を使用するときにだけ、対応するアセンブリがダウンロードされるようにすることができます。  以下のチュートリアルでは、アプリケーション内の特定のアセンブリを "オプション" としてマークを付ける方法、および、共通言語ランタイム \(CLR: Common Language Runtime\) によって要求されたときに、<xref:System.Deployment.Application> 名前空間にあるクラスを使用して、それらのアセンブリをダウンロードする方法を説明します。  
  
> [!NOTE]
>  この手順を使用するには、アプリケーションが完全信頼で実行される必要があります。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のいずれかのコンポーネントが必要です。  
  
-   Windows SDK。  Windows SDK は、Microsoft ダウンロード センターからダウンロードできます。  
  
-   Visual Studio  
  
## プロジェクトの作成  
  
#### オンデマンド アセンブリを使用するプロジェクトを作成するには  
  
1.  ClickOnceOnDemand という名前のディレクトリを作成します。  
  
2.  Windows SDK コマンド プロンプトまたは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] コマンド プロンプトを開きます。  
  
3.  ClickOnceOnDemand ディレクトリに移動します。  
  
4.  次のコマンドを使用して、公開キーと秘密キーのペアを生成します。  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  メモ帳などのテキスト エディターを使用して、`Message` という名前のプロパティ 1 つを持つ `DynamicClass` クラスを定義します。  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-cs[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  このテキストを、使用しているプログラミング言語に応じて `ClickOnceLibrary.cs` または `ClickOnceLibrary.vb` というファイル名で、ClickOnceOnDemand ディレクトリに保存します。  
  
7.  ファイルをアセンブリにコンパイルします。  
  
    ```c#  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb#  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  アセンブリの公開キー トークンを取得するには、次のコマンドを使用します。  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. テキスト エディターを使用して新しいファイルを作成し、次のコードを入力します。  このコードは、必要なときに ClickOnceLibrary アセンブリをダウンロードする Windows フォーム アプリケーションを作成します。  
  
     [!code-cs[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. コード内で <xref:System.Reflection.Assembly.LoadFile%2A> の呼び出しを見つけます。  
  
11. `PublicKeyToken` を、先に取得しておいた値に設定します。  
  
12. ファイルに `Form1.cs` または `Form1.vb` の名前を付けて保存します。  
  
13. これを、次のコマンドを使用して実行可能ファイルにコンパイルします。  
  
    ```c#  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb#  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## アセンブリをオプションとしてマークするには  
  
#### MageUI.exe を使用して ClickOnce アプリケーション内のアセンブリをオプションとしてマークするには  
  
1.  MageUI.exe を使用して、「[チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)」の説明に従ってアプリケーション マニフェストを作成します。  アプリケーション マニフェストに、次の設定を行います。  
  
    -   アプリケーション マニフェストに `ClickOnceOnDemand` という名前を付けます。  
  
    -   **\[Files\]** ページで、ClickOnceLibrary.dll 行の **\[File Type\]** 列を **\[None\]** に設定します。  
  
    -   **\[Files\]** ページで、ClickOnceLibrary.dll 行の **\[Group\]** 列に「`ClickOnceLibrary.dll`」と入力します。  
  
2.  MageUI.exe を使用して、「[チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)」の説明に従って配置マニフェストを作成します。  配置マニフェストに、以下の設定を使用します。  
  
    -   配置マニフェストに `ClickOnceOnDemand` という名前を付けます。  
  
## 新しいアセンブリのテスト  
  
#### オンデマンド アセンブリをテストするには  
  
1.  作成した [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置を Web サーバーにアップロードします。  
  
2.  配置マニフェストの URL を Web ブラウザーに入力して、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] で配置したアプリケーションを Web ブラウザーから起動します。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの名前が `ClickOnceOnDemand` であり、そのアップロード先が adatum.com のルート ディレクトリの場合、入力する URL は次のようになります。  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  メイン フォームが表示されたら、<xref:System.Windows.Forms.Button> をクリックします。  "Hello, World\!" と書かれたメッセージ ボックスが表示されます。  
  
## 参照  
 <xref:System.Deployment.Application.ApplicationDeployment>