---
title: "サンドボックス ソリューションの考慮事項"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SandboxedSolutions"
  - "VS.SharePointTools.Security.SandboxedSolutions"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ファーム ソリューション [Visual Studio での SharePoint 開発]"
  - "サンドボックス ソリューション [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, ファーム ソリューション"
  - "Visual Studio での SharePoint 開発, サンドボックス ソリューション"
ms.assetid: 6c2d2dc6-4acb-4b68-ba94-a61087e8dff0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# サンドボックス ソリューションの考慮事項
  *サンドボックス ソリューション*は、サイト コレクションのユーザーが独自のカスタム コード ソリューションをアップロードできるようにする Microsoft SharePoint 2010 の機能です。  たとえば、一般的なサンドボックス化ソリューションとして、ユーザーは独自の Web パーツをアップロードすることができます。  
  
 サンドボックス SharePoint アプリケーションは、Web ファームの限られた部分にのみアクセスできる安全で監視されたプロセスで実行されます。  Microsoft SharePoint 2010 では、フィーチャー、ソリューション ギャラリー、ソリューション モニタリング、および検証フレームワークの組み合わせによってサンドボックス ソリューションが実現されます。  
  
## プロジェクトの信頼レベルの指定  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は、*Sandboxed Solution* というブール型のプロジェクト プロパティによってサンドボックス ソリューションをサポートします。  このプロパティはプロジェクト内でいつでも設定できるほか、**SharePoint カスタマイズ ウィザード** でプロジェクトを作成するときに指定することもできます。  
  
> [!NOTE]  
>  プロジェクトの作成後に *Sandboxed Solution* プロパティを変更すると、検証エラーが発生することがあります。  
  
 ソリューションは *Sandboxed Solution* のプロパティが **false** に設定されている場合、または **\[ファーム ソリューションとして配置する\]** オプションを選択するとファーム スコープのソリューションと見なされます。  ただし、ソリューションは *Sandboxed Solution* のプロパティが **true** に設定されている場合、またはウィザードの **\[サンドボックス ソリューションとして配置する\]** オプションを選択するとファーム ソリューションと異なります。  
  
## SharePoint サイト階層  
 サンドボックス ソリューションのしくみを理解するには、まず SharePoint サイトのスコープが階層構造になっていることを認識しておく必要があります。  最上位の要素は Web ファームで、それ以外の要素は Web ファームに従属します。  
  
 Web ファーム  
  
 Web アプリケーション A  
  
 サイト コレクション A1  
  
 サイト A1a  
  
 Web アプリケーション B  
  
 サイト コレクション B1  
  
 サイト B1a  
  
 サイト B1b  
  
 サイト コレクション B2  
  
 サイト B2a  
  
 これを見るとわかるように、Web ファームには 1 つ以上の Web アプリケーションを含めることができます。さらに、Web アプリケーションには 1 つ以上のサイト コレクションを含めることができ、サイト コレクションにはサブサイトを含めることができます。  特定のサイト コレクションに対して行った変更は、そのサイト コレクションにのみ影響し、他のサイト コレクションには影響しません。  ただし、Web ファーム レベルで行った変更は、そのファーム上のすべてのサイト コレクションに影響します。  
  
 Windows SharePoint Services \(WSS\) 3.0 では、ソリューションの配置はファーム レベルに限られますが、[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] では、ファーム レベル \(ファーム ソリューション\) だけでなく、サイト コレクション レベル \(サンドボックス ソリューション\) でもソリューションを配置できます。  
  
## サンドボックス ソリューションが必要な理由  
 WSS 3.0 では、ソリューションをファーム レベルでしか配置できませんでした。  万一有害なソリューションや安定性を損なうソリューションが配置されると、Web ファーム全体と、その下で実行されている他のすべてのサイト コレクションおよびアプリケーションにまで影響が及ぶことになります。  一方、サンドボックス ソリューションを使用すると、ファームのサブエリア、つまり、特定のサイト コレクションにソリューションを配置できます。  また、二重の保護対策として、メインの [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] プロセス \(w3wp.exe\) にはソリューションのアセンブリが読み込まれないようになっています。  ソリューションは、代わりに、独立したプロセス \(SPUCWorkerProcess.exe\) に読み込まれます。  このプロセスは監視され、有害な動作を実行するサンドボックス ソリューション \(CPU サイクルを消費する短いループの実行など\) からファームを保護するためにクォータとスロットリングを実装します。  
  
## サイト コレクションのソリューション ギャラリー  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 に「サイト コレクションのソリューション ギャラリーとして」既知の機能があります。SharePoint 2010 のサーバーの全体管理ページからまたは **\[サイトの操作\]** メニューを開き、" **\[サイトの設定\]** をクリックします、SharePoint サイトの **\[ ギャラリー\]** で **\[ソリューション\]** リンクをクリックすると、この機能にアクセスできます。  ソリューション ギャラリーは、ソリューションのリポジトリです。サイト コレクションの管理者は、このリポジトリを使用して、サイト コレクション内のソリューションを管理することができます。  
  
 ソリューション ギャラリーは、SharePoint サイトのルート Web に格納されるドキュメント ライブラリです。  サイト ギャラリーは、サイト テンプレートに代わる機能であり、ソリューション パッケージをサポートします。  アップロードされた SharePoint ソリューション パッケージ \(.wsp\) ファイルは、サンドボックス ソリューションとして処理されます。  
  
## サンドボックス ソリューションの制限  
 サンドボックス ソリューションが配置されると、それが使用できる SharePoint の機能は、セキュリティ上の脆弱性を低減するため制限されます。  たとえば、次のような制限があります。  
  
-   サンドボックス ソリューションが使用できるソリューション要素は、配置可能なソリューション要素のサブセットに限定されます。  脆弱性が懸念される SharePoint プロジェクト テンプレート \(サイト定義、ワークフローなど\) は利用できません。  
  
-   サンドボックス ソリューションのコードは、メインの [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] アプリケーション プール \(w3wp.exe\) のプロセスとは独立した別個のプロセス \(SPUCWorkerProcess.exe\) で実行されます。  
  
-   マップされたフォルダーをプロジェクトに追加することはできません。  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] アセンブリ Microsoft.Office.Server の型はサンドボックス ソリューションで使用できません。  また、サンドボックス ソリューションに使用できるのは、[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] アセンブリ Microsoft.SharePoint の型のみです。  
  
 SharePoint ソリューションをサンドボックス ソリューションとして指定しても、SharePoint サーバーそのものは影響を受けません。SharePoint プロジェクトを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] から SharePoint に配置する方法とバインド先のアセンブリが指定されるだけです。  これは生成される .wsp ファイルには影響せず、*Sandboxed Solution* プロパティに直接関連付けられているデータは .wsp ファイルには含まれていません。  
  
## サンドボックス ソリューションの機能と要素  
 サンドボックス ソリューションでは、次の機能および要素がサポートされています。  
  
-   コンテンツ タイプ\/フィールド  
  
-   カスタム動作  
  
-   宣言型のワークフロー  
  
-   イベント レシーバー  
  
-   フィーチャーのコールアウト  
  
-   リスト定義  
  
-   リスト インスタンス  
  
-   モジュール\/ファイル  
  
-   Navigation  
  
-   Onet.xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   `System.Web.UI.WebControls.WebParts.WebPart` から派生するすべての Web パーツのサポート  
  
-   Web パーツ  
  
-   WebTemplate フィーチャー要素 \(Webtemp.xml ではなく\)  
  
-   ビジュアル Web パーツ  
  
 サンドボックス ソリューションでは、次の機能および要素はサポートされていません。  
  
-   アプリケーション ページ  
  
-   カスタム動作グループ  
  
-   ファーム スコープの機能  
  
-   `HideCustomAction` 要素  
  
-   Web アプリケーション スコープの機能  
  
-   コードを含んだワークフロー  
  
## 参照  
 [サンドボックス ソリューションとファーム ソリューションの違い](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  