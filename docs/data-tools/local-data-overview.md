---
title: "ローカル データの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Access, .mdb ファイル (Visual Studio の)"
  - "データ [Visual Studio], local"
  - "データ アクセス [Visual Studio], トラブルシューティング"
  - "ローカル データ"
  - "LocalDB"
  - "SQL Express"
  - "SQL Server Compact"
  - "SQL Server Express"
  - "SQL Server LocalDB"
  - "SQL Server, ローカル データ"
  - "SQLEXPRESS"
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
caps.handback.revision: 66
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# ローカル データの概要
ローカル データを使用すると、別のサーバーのデータベースではなく、ローカル コンピューター上のデータベース ファイルにアプリケーションを接続します。  たとえば、Visual Studio で開発中のアプリケーションを次のローカル データベース ファイルに接続できます。  
  
-   SQL Server Express LocalDB のデータベース ファイル \(.mdf\)  
  
-   SQL Server Express データベース ファイル \(.mdf\)  
  
-   Microsoft Access データベース ファイル \(.mdb\)  
  
 次の表に、アプリケーションをローカル データに接続する方法を説明するトピックへのリンクを示します。  
  
|トピック|説明|  
|----------|--------|  
|[チュートリアル: Visual Studio でのローカル データベース ファイルの作成](../data-tools/create-a-sql-database-by-using-a-designer.md)|データ機能のテストとアプリケーションのビルドを行うために使用できるローカル データベース ファイルを作成するための手順を示します。|  
|[チュートリアル: ローカル データベース ファイル内のデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)|簡単な Windows アプリケーションを作成する際に SQL Server Express の LocalDB データベースに接続するための手順を示します。|  
|[チュートリアル: Access データベース内のデータへの接続 \(Windows フォーム\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Microsoft Access データベースへの接続の詳細な手順を提供します。|  
|[方法: Northwind データベースへの接続](../data-tools/how-to-connect-to-the-northwind-database.md)|[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]、SQL Server Compact、SQL Server Express、および Access の Northwind サンプル データベースに接続する方法の詳細について説明します。|  
  
 データ ソースを作成してローカル データ ファイルにアクセスするように構成すると、他のソースのデータと同じテクノロジとオブジェクトを使用してデータを操作できます。  詳細については、「[データ アプリケーションの作成](../data-tools/creating-data-applications.md)」を参照してください。  
  
## データベースのアプリケーションへの統合  
 ローカル データに接続する場合は、データベース ファイルに接続するだけでなく、それをアプリケーションに統合できます。  たとえば、**\[プロジェクト\]** メニューを開き、既存の .sdf ファイル、.mdf ファイル、または .mdb ファイルを探して、ファイルをプロジェクトに追加できます。  
  
 ローカル データ ファイルを追加すると、型指定されたデータセットおよびアプリケーションのデータベース ファイルを指す接続文字列が動的に作成されます。  データベース ファイルをプロジェクトに追加するときは、**データ ソース構成ウィザード**を使用して、含むオブジェクトを指定します。  
  
> [!NOTE]
>  .sdf ファイル、.mdf ファイル、または .mdb ファイルをファイル エクスプローラーから**ソリューション エクスプローラー**にドラッグすると、接続が自動的に構成され、**データ ソース構成ウィザード**が開始されます。  次にアプリケーションで使用するオブジェクトを指定できます。  
  
 **データ ソース構成ウィザード**を使用してローカル データ ファイルのデータ ソースを作成すると、プロジェクトにファイルを含めるように求めるダイアログが表示されます。  プロジェクトにファイルを含めない場合、アプリケーションには実際のデータ ファイルではなく、ハードコーディングされたパスを指す接続文字列だけが含められます。  詳細については、「[方法 : プロジェクトでローカル データ ファイルを管理する](../data-tools/how-to-manage-local-data-files-in-your-project.md)」を参照してください。  
  
 ウィザードの作業が完了すると、データベース ファイルとデータセットが**ソリューション エクスプローラー**または**データベース エクスプローラー**に表示され、指定したデータベース オブジェクトが **\[データ ソース\]** ウィンドウに表示されます。  **\[データ ソース\]** ウィンドウからフォームに項目をドラッグして、基になるデータにバインドするコントロールを作成できます。  **\[データ\]** メニューの **\[データ ソースの表示\]** を選択して、**\[データ ソース\]** ウィンドウを開きます。  詳細については、「[Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)」を参照してください。  
  
## データベース ファイルの使用  
 既存のデータベース ファイル \(.mdf\) を Visual Studio で使用する前に、ファイルを [!INCLUDE[sql_Denali_short](../data-tools/includes/sql_denali_short_md.md)] のデータベース ファイルに変換する必要があります。  既存のデータベース ファイルに接続する場合には、アップグレードするかどうかをたずねるメッセージ ボックスが表示されます。  
  
> [!IMPORTANT]
>  データベース ファイル \(.mdf\) をアップグレードすると、それを SQL Server の以前のバージョンでは開くことができません。  
  
 **\[SQL Server インスタンス名\]** が SQLEXPRESS に設定され、SQL Server 2008 Express がインストールされている場合には、データベース ファイル \(.mdf\) を変換する必要はありません。  Visual Studio 2010 がインストールされている場合、SQL Server 2008 Express はインストールされています。  このデータベース ファイルのインスタンス名を変更するには、Visual Studio を開き、**\[接続の追加\]** ダイアログ ボックスを開いて、サーバー名として「`.\SQLEXPRESS`」を指定します。次に、データベースまたはデータベース ファイルの名前を指定します。  
  
## SQL Server Express の LocalDB と SQL Server Express  
 Visual Studio の各プロジェクトに、サービス ベースのデータベース ファイル \(.mdf\) を追加できます。  Visual Studio のデザイナーを使用して、テーブルなどのデータベース オブジェクトをデザインし、クエリを実行することができます。  
  
 Visual Studio でサービス ベースのデータベースを作成した場合、データベース ファイル \(.mdf\) へのアクセスには SQL Server Express LocalDB エンジンが使用されます。Visual Studio の以前のバージョンでは SQL Server Express エンジンが使用されていました。  
  
 SQL Server Express LocalDB は SQL Server の軽量バージョンであり、SQL Server データベースと同様の多くの方法でプログラミングできます。  SQL Server Express LocalDB はユーザー モードで実行され、より少ない必須コンポーネントでよりすばやくインストールでき、構成は不要です。  
  
> [!NOTE]
>  SQL Server Express LocalDB の詳細については、Microsoft Web サイトの「[Introducing LocalDB, an Improved SQL Express \(強化された SQL Express、LocalDB の概要\)](http://go.microsoft.com/fwlink/?LinkId=234375)」および「[LocalDB: Where is My Database? \(LocalDB: My Database はどこにあるか\)](http://go.microsoft.com/fwlink/?LinkId=234376)」を参照してください。  
  
 Visual Studio では、SQL Server Express LocalDB に代えて、既定で SQL Server Express を使用できます。  メニュー バーの **\[ツール\]**、**\[オプション\]** の順にクリックします。  **\[データベース ツール\]** のノードの下で、**\[データ接続\]** を選択します。  **\[SQL Server インスタンス名\]** ボックスに、「`SQLEXPRESS`」と入力します。  または、SQL Server インスタンス名に他の値を入力することもできます \(たとえば、「`SQL2008`」\)。  
  
 SQL Server Express LocalDB と SQL Server Express エンジンの違いを次の表に示します。  
  
||SQL Server Express LocalDB|SQL Server Express|  
|-|--------------------------------|------------------------|  
|サービス ベースのデータベースを作成するときのデータベースの種類|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] および [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] では、SQL Server Express LocalDB|Visual Studio 2010 以前では、SQL Server Express|  
|\[ツール\] と \[オプション\] での SQL Server のインスタンス名|\(LocalDB\)\\v11.0|SQLEXPRESS|  
|接続文字列のデータ ソースの値|\(LocalDB\)\\v11.0|.\\SQLEXPRESS|  
|接続文字列の AttachDbFilename の値|ファイル パス|ファイル パス|  
|ユーザー インスタンスは必須 \(接続文字列で "User Instance\=True"\)|いいえ|○|  
|データベース ファイルの拡張子|.mdf|.mdf|  
  
## SQL Server Express LocalDB の利点  
  
-   SQL Server Express LocalDB は、SQL Server Express LocalDB で有効になる機能について、SQL Server のサービス ベース エディションと互換性があります。  SQL Server では、特にアップグレード手順を実行することなく、SQL Server Express LocalDB から SQL Server または SQL Azure にデータベースまたは Transact\-SQL コードを移行できます。  このため、SQL Server Express LocalDB を使用して、SQL Server のすべてのエディションを対象とするアプリケーションを開発することができます。  
  
-   SQL Server Express LocalDB では、SQL Server の上位エディションと同じクエリ オプティマイザーおよびクエリ プロセッサがサポートされます。  
  
## 各プロジェクトはデータベースの 2 つのコピーを含む  
 プロジェクトをビルドしたときに、ルート プロジェクト フォルダーから出力の **bin** フォルダーにデータベース ファイルがコピーされる場合があります。  この動作は、ファイルの **\[出力ディレクトリにコピー\]** プロパティに依存し、そのプロパティの既定値は、使用しているデータベース ファイルの種類によって異なります。  
  
 **bin** フォルダーを表示するには、**ソリューション エクスプローラー**で **\[すべてのファイルを表示\]** を選択します。  
  
> [!NOTE]
>  **\[出力ディレクトリにコピー\]** プロパティは、Web プロジェクトまたは C\+\+ プロジェクトには適用されません。  
  
 ルート プロジェクト フォルダー内のデータベース ファイルは、**サーバー エクスプローラー**や**データベース エクスプローラー**またはその他の [Visual Database Tools](http://msdn.microsoft.com/ja-jp/6b145922-2f00-47db-befc-bf351b4809a1) を使用してデータベースのスキーマまたはデータを編集する場合のみ変更されます。  
  
 アプリケーションの開発時にデータを変更する場合、**bin** フォルダーのデータベースを変更しています。  たとえば、F5 キーを押してアプリケーションをデバッグすると、そのフォルダー内のデータベースに接続されます。  
  
|**\[出力ディレクトリにコピー\]** プロパティの値|動作|  
|----------------------------------|--------|  
|**\[新しい場合はコピーする\]** \(.sdf ファイルの既定値\)|データベース ファイルは、プロジェクトを初めてビルドするときに、プロジェクト ディレクトリから **bin** ディレクトリにコピーされます。  その後、プロジェクトを再びビルドするたびに、ファイルの **\[更新日時\]** プロパティが比較されます。  プロジェクト フォルダーのファイルの方が新しい場合は、前のファイルを置き換えて **bin** フォルダーにコピーされます。  それ以外の場合には、ファイルはコピーされません。 **Caution:**  この値は、.mdb ファイルまたは .mdf ファイルには推奨されません。  データベース ファイルはデータが変更されていない場合でも変更される場合があります。  単に接続を開く \(たとえば、**サーバー エクスプローラー**で **\[テーブル\]** ノードを展開する\) だけでも、ファイルが更新済みとマークされる場合があります。|  
|**\[常にコピーする\]** \(.mdf ファイルおよび .mdb ファイルの既定値\)|データベース ファイルは、アプリケーションをビルドするたびに、プロジェクト ディレクトリから **bin** ディレクトリにコピーされます。  出力フォルダー内のデータ ファイルに行った変更は、次にアプリケーションを実行したときに上書きされます。|  
|**\[コピーしない\]**|システムは、**bin** ディレクトリのファイルをオーバーライドすることはありません。  アプリケーションは、出力ディレクトリ内のデータベース ファイルを指す接続文字列を動的に作成します。  したがって、出力ディレクトリ内のデータとプロジェクト ディレクトリのデータを一致させるためには、出力ディレクトリに手動でファイルをコピーする必要があります。|  
  
## ローカル データの一般的な問題  
 次の表は、ローカル データ ファイルを使用するときに発生する可能性のある一般的な問題を示しています。  
  
|懸案事項|説明|  
|----------|--------|  
|アプリケーションをテストしてデータを変更し、次回アプリケーションを実行すると必ず変更内容が失われる|**\[出力ディレクトリにコピー\]** プロパティの値が **\[新しい場合はコピーする\]** または **\[常にコピーする\]** です。  出力フォルダーのデータベース \(アプリケーションをテストする際に変更されるデータベース\) は、プロジェクトをビルドするたびに上書きされます。  詳細については、「[方法 : プロジェクトでローカル データ ファイルを管理する](../data-tools/how-to-manage-local-data-files-in-your-project.md)」を参照してください。|  
|データ ファイルがロックされているというメッセージが表示される。|Access \(.mdb ファイル\) : Access などの別のプログラムでファイルが開かれていないことを確認します。<br /><br /> SQL Server Express \(.mdf ファイル\) : Visual Studio IDE の外部でデータ ファイルをコピー、移動、または名前を変更しようとすると、SQL Express はデータ ファイルをロックします。|  
|複数のユーザーが同じデータベースを同時にアクセスしようとすると、アクセスは拒否されます。|Visual Studio は、SQL Server Express の機能である*ユーザー インスタンス*を活用して、各ユーザーに対して SQL Server のインスタンスを個別に作成します。  1 人のユーザーがファイルにアクセスすると、その後にアクセスするユーザーは接続できません。  この問題は、インターネット インフォメーション サービス \(IIS\) は一般に個別のアカウントで実行されるので、ASP.NET 開発サーバーと IIS で Web アプリケーションを実行しようとする場合などに発生します。|  
  
## 参照  
 [チュートリアル: ローカル データベース ファイル内のデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)   
 [チュートリアル: Access データベース内のデータへの接続 \(Windows フォーム\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)