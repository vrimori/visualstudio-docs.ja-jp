---
title: "チュートリアル : デザイナーを使用し、ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロードする | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "ClickOnce 配置, グローバリゼーション"
  - "ClickOnce 配置, ローカリゼーション"
  - "ClickOnce, オンデマンド ダウンロード"
  - "ローカリゼーション, Windows フォーム"
  - "チュートリアル, ローカリゼーション"
  - "Windows フォーム, グローバリゼーション"
  - "Windows フォーム, ローカリゼーション"
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# チュートリアル : デザイナーを使用し、ClickOnce 配置 API で必要に応じてサテライト アセンブリをダウンロードする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

サテライト アセンブリを使用すると、複数のカルチャに対して Windows フォーム アプリケーションを構成できます。  *サテライト アセンブリ*とは、アプリケーションの既定のカルチャ以外のカルチャ用アプリケーション リソースを含むアセンブリのことです。  
  
 「[ClickOnce アプリケーションのローカライズ](../deployment/localizing-clickonce-applications.md)」で説明しているように、同じ [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置内に複数のカルチャ用の複数のサテライト アセンブリを含めることができます。  既定では、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] により配置に含まれるすべてのサテライト アセンブリがクライアント コンピューターにダウンロードされます。ただし、多くの場合、1 つのクライアントに必要なサテライト アセンブリは 1 つだけです。  
  
 このチュートリアルでは、サテライト アセンブリをオプションとしてマークする方法、および現在のカルチャ設定にクライアント コンピューターが必要とするアセンブリのみをダウンロードする方法について説明します。  
  
> [!NOTE]
>  次のコード例は、テストを目的としているため、プログラム内でカルチャを `ja-JP` に設定しています。  このコードを運用環境用に調整する方法については、このトピックの「次の手順」セクションを参照してください。  
  
### サテライト アセンブリをオプションとしてマークするには  
  
1.  プロジェクトをビルドします。  これにより、ローカライズの対象としているすべてのカルチャについて、サテライト アセンブリが生成されます。  
  
2.  ソリューション エクスプローラーでプロジェクト名を右クリックし、**\[プロパティ\]** をクリックします。  
  
3.  **\[発行\]** タブをクリックし、**\[アプリケーション ファイル\]** をクリックします。  
  
4.  **\[すべてのファイルを表示\]** チェック ボックスをオンにして、サテライト アセンブリを表示します。  既定では、すべてのサテライト アセンブリが配置対象に含められ、このダイアログ ボックスに表示されます。  
  
     サテライト アセンブリの名前は、"*isoCode*\\ApplicationName.resources.dll" という形式で付けられます。*isoCode* は RFC 1766 形式の言語識別子を表します。  
  
5.  各言語識別子の **\[ダウンロード グループ\]** ボックスの一覧で、**\[新規作成\]** をクリックします。  ダウンロード グループ名の入力を求めるメッセージが表示されたら、言語識別子を入力します。  たとえば、日本語のサテライト アセンブリであれば、ダウンロード グループ名として「`ja-JP`」を指定します。  
  
6.  **\[アプリケーション ファイル\]** ダイアログ ボックスを閉じます。  
  
### 必要に応じてサテライト アセンブリをダウンロードするには \(C\#\)  
  
1.  Program.cs ファイルを開きます。  このファイルがソリューション エクスプローラーに表示されない場合は、プロジェクトを選択し、**\[プロジェクト\]** メニューの **\[すべてのファイルを表示\]** をクリックします。  
  
2.  該当するサテライト アセンブリをダウンロードし、アプリケーションを起動するには、次のコードを使用します。  
  
     [!code-cs[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]  
  
### 必要に応じてサテライト アセンブリをダウンロードするには \(Visual Basic\)  
  
1.  アプリケーションの **\[プロパティ\]** ウィンドウで、**\[アプリケーション\]** タブをクリックします。  
  
2.  タブ ページの一番下にある **\[アプリケーション イベントの表示\]** をクリックします。  
  
3.  ApplicationEvents.VB ファイルの先頭に、次の Imports ステートメントを追加します。  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]  
  
4.  `MyApplication` クラスに次のコードを追加します。  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]  
  
## 次の手順  
 コード例を見ると、<xref:System.Threading.Thread.CurrentUICulture%2A> が特定の値に設定されています。しかし、運用環境では、クライアント コンピューターに適切な値が既定で設定されるため、この行は削除する必要があります。  たとえば、アプリケーションを日本語のクライアント コンピューターで実行する場合、既定では <xref:System.Threading.Thread.CurrentUICulture%2A> が `ja-JP` になります。  ここでは、アプリケーションの配置前にサテライト アセンブリをテストするという趣旨でプログラムから設定しています。  
  
## 参照  
 [チュートリアル : ClickOnce 配置 API を使用して必要に応じてサテライト アセンブリをダウンロードする](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [ClickOnce アプリケーションのローカライズ](../deployment/localizing-clickonce-applications.md)