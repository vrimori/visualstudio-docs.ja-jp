---
title: "Windows フォーム アプリケーションでのデータへの接続 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "System.Data.SqlClient.SqlConnection"
  - "System.Data.Odbc.OdbcConnection"
  - "System.Data.OleDb.OleDbConnection"
  - "System.Data.OracleClient.OracleConnection"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "接続 (データベースに), ADO.NET 接続"
  - "接続オブジェクト"
  - "接続オブジェクト, ツール"
  - "接続オブジェクト, 型"
  - "接続プール, ADO.NET 接続"
  - "接続文字列 [Visual Studio], ADO.NET"
  - "接続, 接続の概要"
  - "接続, デザイン時"
  - "データ [Visual Studio], 接続"
  - "データ アダプター, 接続"
  - "データベース接続 [Visual Studio], ADO.NET"
  - "データベース [Visual Studio], 接続"
  - "デザイン時の接続"
  - "動的プロパティ, ADO.NET 接続"
  - "OleDbConnection クラス, ADO.NET 接続オブジェクト"
  - "SqlConnection クラス, ADO.NET 接続オブジェクト"
  - "TableAdapter, 接続"
  - "トランザクション, ADO.NET"
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Windows フォーム アプリケーションでのデータへの接続
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] には、データベース、Web サービス、オブジェクトなどのさまざまなソースのデータにアプリケーションを接続するためのツールが用意されています。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でデータ デザイン ツールを使用している場合は、フォームまたはコンポーネント用に接続オブジェクトを明示的に作成する必要はあまりありません。  通常、接続オブジェクトは、データ ウィザードの 1 つを完了するか、データ オブジェクトをフォームにドラッグした結果として作成されます。  アプリケーションをデータベース、Web サービス、またはオブジェクトのデータに接続するには、[ウィンドウ](../Topic/Data%20Sources%20Window.md)から **\[新しいデータ ソースの追加\]** を選択して、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を実行します。  
  
 次の図は、TableAdapter クエリを実行してデータに接続し、データをフェッチして Windows アプリケーションのフォームに表示する場合の標準的な操作の流れを示しています。  
  
 ![クライアント アプリケーションのデータ フロー](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 状況によっては、データ デザイン ツールを利用せずに接続オブジェクトを作成すると便利です。  プログラムによって接続を作成する方法の詳細については、「[データ ソースへの接続](../Topic/Connecting%20to%20a%20Data%20Source%20in%20ADO.NET.md)」を参照してください。  
  
> [!NOTE]
>  Web アプリケーションをデータに接続する方法の詳細については、「[ASP.NET Data Access Content Map](http://msdn.microsoft.com/ja-jp/f9219396-a0fa-481f-894d-e3d9c67d64f2)」を参照してください。  
  
## Windows フォーム アプリケーションをデータに接続するためのチュートリアル  
 次のチュートリアルでは、Windows フォーム アプリケーションでのデータへの接続に関連する手順を示しています。  
  
-   [チュートリアル: データベース内のデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)  
  
-   [チュートリアル: ローカル データベース ファイル内のデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)  
  
-   [チュートリアル: Web サービス内のデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Web%20Service%20\(Windows%20Forms\).md)  
  
-   [チュートリアル: オブジェクトのデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)  
  
-   [チュートリアル: Access データベース内のデータへの接続 \(Windows フォーム\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## 接続の作成  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、接続は **\[接続の追加\] または \[接続の変更\]** ダイアログ ボックスを使用して設定します。  **\[接続の追加\]** ダイアログ ボックスは、いずれかのデータ ウィザードか、[サーバー エクスプローラーまたはデータベース エクスプローラー](../Topic/Server%20Explorer.md)で接続を編集または作成する際、あるいは **\[プロパティ\]** ウィンドウで接続プロパティを編集する際に表示されます。  
  
 次のいずれかの操作を実行すると、データ接続が自動的に構成されます。  
  
|動作|説明|  
|--------|--------|  
|[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)を実行する。|**データ ソース構成ウィザード**でデータベース パスを選択すると、接続が構成されます。  詳細については、「[方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)」を参照してください。|  
|[TableAdapter 構成ウィザード](../Topic/TableAdapter%20Configuration%20Wizard.md)を実行する。|**TableAdapter 構成ウィザード**内で接続が作成されます。  詳細については、「[方法 : TableAdapter を作成する](../data-tools/create-and-configure-tableadapters.md)」を参照してください。|  
|[TableAdapter クエリの構成ウィザード](../data-tools/editing-tableadapters.md)を実行する。|**TableAdapter クエリの構成ウィザード**内で接続が作成されます。  詳細については、「[方法 : TableAdapter クエリを作成する](../data-tools/how-to-create-tableadapter-queries.md)」を参照してください。|  
|[ウィンドウ](../Topic/Data%20Sources%20Window.md)からフォームまたは[Component Designer](../Topic/Component%20Designer.md)に項目をドラッグする。|**\[データ ソース\]** ウィンドウから **Windows フォーム デザイナー**または**コンポーネント デザイナー**に項目をドラッグすると、接続オブジェクトが作成されます。  詳細については、「[Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)」を参照してください。|  
|新しいデータ接続を[サーバー エクスプローラーまたはデータベース エクスプローラー](../Topic/Server%20Explorer.md)に追加する。|データ ウィザード内の使用可能な接続の一覧に、**サーバー エクスプローラーまたはデータベース エクスプローラー**のデータ接続が表示されます。|  
  
## 接続文字列  
 コンパイルされたアプリケーションまたはアプリケーション構成ファイルに接続文字列を格納できます。  詳細については、「[方法: 接続文字列を保存および編集する](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md)」を参照してください。  
  
## 接続情報とセキュリティ  
 接続を開くには重要なリソース \(データベース\) にアクセスする必要があるため、多くの場合、接続の設定や操作にはセキュリティ上の問題があります。  
  
 アプリケーション、およびアプリケーションからデータ ソースへのアクセスを保護する方法は、システムのアーキテクチャによって異なります。  たとえば、Web ベースのアプリケーションでは、通常、ユーザーはインターネット インフォメーション サービス \(IIS\) に匿名でアクセスできるため、セキュリティ資格情報を提示しません。  この場合、アプリケーションは独自のログオン情報を保持し、特定のユーザー情報ではなくこの情報を使用して接続を開き、データベースにアクセスします。  
  
> [!IMPORTANT]
>  接続文字列の詳細 \(パスワードなど\) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。  データベースへのアクセスを制御する方法としては、Windows 統合セキュリティを使用する方が安全です。  詳細については、「[接続情報の保護](../Topic/Protecting%20Connection%20Information.md)」を参照してください。  
  
 イントラネットまたは多階層アプリケーションでは、Windows、IIS、および SQL Server によって提供される統合セキュリティ オプションを利用できます。  このモデルでは、ローカル ネットワークに対するユーザーの認証資格情報がデータベース リソースへのアクセスにも使用され、明示的なユーザー名やパスワードは接続文字列で使用されません。  通常、アクセス許可はデータベース サーバー コンピューター上でグループを使用して確立されるため、データベースにアクセスする可能性があるすべてのユーザーに対して個別にアクセス許可を設定する必要はありません。  このモデルでは、接続用のログオン情報を格納する必要はなく、接続文字列情報を保護するための追加の手順は必要ありません。  
  
 セキュリティの詳細については、次のトピックを参照してください。  
  
-   [ADO.NET アプリケーションのセキュリティ保護](../Topic/Securing%20ADO.NET%20Applications.md)  
  
-   [Windows フォームにおけるファイルおよびデータへのより安全なアクセス](../Topic/More%20Secure%20File%20and%20Data%20Access%20in%20Windows%20Forms.md)  
  
## サーバー エクスプローラーまたはデータベース エクスプローラーでのデザイン時接続  
 **サーバー エクスプローラーまたはデータベース エクスプローラー**には、データ ソースへのデザイン時接続を作成する方法が用意されています。  これにより、使用可能なデータ ソースの参照、データ ソースに含まれるテーブルや列などの要素に関する情報の表示、データベース要素の編集および作成を行うことができます。  
  
 **サーバー エクスプローラーまたはデータベース エクスプローラー**で使用できる接続は、アプリケーションでは直接使用されません。  これらの接続は、デザイン時にデータベースを操作するために [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で使用されます。  詳細については、「[Visual Database Tools](http://msdn.microsoft.com/ja-jp/6b145922-2f00-47db-befc-bf351b4809a1)」を参照してください。  
  
 たとえば、デザイン時に、**サーバー エクスプローラーまたはデータベース エクスプローラー**を使用してデータベースへの接続を作成する場合があります。  後でフォームをデザインするときに、データベースを参照し、テーブルから列を選択して[データセット デザイナー](../data-tools/creating-and-editing-typed-datasets.md)にドラッグできます。  これにより、データセットに [TableAdapter](../data-tools/tableadapter-overview.md) が作成されます。  また、新しく作成された TableAdapter に含まれる新しい接続オブジェクトも作成されます。  
  
 デザイン時接続に関する情報は、特定のプロジェクトやソリューションから独立してローカル コンピューターに格納されます。  このため、アプリケーションでの作業中にデザイン時接続を確立すると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で作業するたびに、接続先のサーバーが使用可能である限り、**サーバー エクスプローラーまたはデータベース エクスプローラー**に常にその接続が表示されます。  詳細については、「[How to: Connect to a Database from Server Explorer](http://msdn.microsoft.com/ja-jp/7c1c3067-0d77-471b-872b-639f9f50db74)」を参照してください。  
  
 [!INCLUDE[SQLObjectExplorer](../data-tools/includes/sqlobjectexplorer_md.md)]  
  
## 参照  
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [チュートリアル: データベース内のデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)   
 [ASP.NET Data Access Content Map](http://msdn.microsoft.com/ja-jp/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)