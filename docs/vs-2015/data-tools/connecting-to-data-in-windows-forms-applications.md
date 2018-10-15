---
title: フォームのアプリケーションを Windows でのデータへの接続 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- System.Data.SqlClient.SqlConnection
- System.Data.Odbc.OdbcConnection
- System.Data.OleDb.OleDbConnection
- System.Data.OracleClient.OracleConnection
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- connection objects, tools for working with
- OleDbConnection class, ADO.NET connection objects
- databases [Visual Studio], connecting to
- data adapters, connections
- connection pooling, ADO.NET connections
- connection strings [Visual Studio], ADO.NET
- connection objects, types of
- dynamic properties, ADO.NET connections
- connections, about connections
- data [Visual Studio], connecting
- design-time connections
- connections, design-time
- TableAdapters, connections
- connection objects
- SqlConnection class, ADO.NET connection objects
- connecting to databases, ADO.NET connections
- transactions, ADO.NET
- database connections [Visual Studio], ADO.NET
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d8da35b32f3dd25bd7ed47b25f722c6b0aa21ac7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208950"
---
# <a name="connecting-to-data-in-windows-forms-applications"></a>Windows フォーム アプリケーションでのデータへの接続
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] には、データベース、Web サービス、オブジェクトなどのさまざまなソースのデータにアプリケーションを接続するためのツールが用意されています。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] でデータ デザイン ツールを使用している場合は、フォームまたはコンポーネント用に接続オブジェクトを明示的に作成する必要はあまりありません。 通常、接続オブジェクトは、データ ウィザードの 1 つを完了するか、データ オブジェクトをフォームにドラッグした結果として作成されます。 アプリケーションをデータベース、web サービス、またはオブジェクトにデータを接続するには、実行、[データ ソース構成ウィザード](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)を選択して**新しいデータ ソースの追加**から、 [データソースウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 次の図は、TableAdapter クエリを実行してデータに接続し、データをフェッチして Windows アプリケーションのフォームに表示する場合の標準的な操作の流れを示しています。  
  
 ![クライアント アプリケーションでのデータ フロー](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 状況によっては、データ デザイン ツールを利用せずに接続オブジェクトを作成すると便利です。 プログラムによる接続の作成方法の詳細については、次を参照してください。[データ ソースに接続する](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e)します。  
  
> [!NOTE]
>  Web アプリケーションをデータに接続する方法については、次を参照してください。 [ASP.NET データ アクセス コンテンツ マップ](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2)します。  
  
## <a name="walkthroughs-for-connecting-windows-forms-applications-to-data"></a>Windows フォーム アプリケーションをデータに接続するためのチュートリアル  
 次のチュートリアルでは、Windows フォーム アプリケーションでのデータへの接続に関連する手順を示しています。  
  
-   [チュートリアル: データベース (Windows フォーム) 内のデータへの接続](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)  
  
-   [チュートリアル: ローカル データベース ファイル内のデータへの接続 (Windows フォーム)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)  
  
-   [チュートリアル: Web サービス (Windows フォーム) のデータへの接続](http://msdn.microsoft.com/library/079fb9b0-c733-40c1-acd1-d0d68834354d)  
  
-   [チュートリアル: データ オブジェクト (Windows フォーム) に接続します。](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)  
  
-   [Access データベース内のデータへの接続 (Windows フォーム)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## <a name="creating-connections"></a>接続の作成  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]を使用して接続が構成されて、**接続の追加/変更** ダイアログ ボックス。 **接続の追加**いずれかのデータ ウィザード内の接続を作成または編集する場合、ダイアログ ボックスが表示されますまたは[サーバー エクスプ ローラー/データベース エクスプ ローラー](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d)または接続文字列プロパティを編集しているときに**プロパティ**ウィンドウ。  
  
 次のいずれかの操作を実行すると、データ接続が自動的に構成されます。  
  
|動作|説明|  
|------------|-----------------|  
|実行、[データ ソース構成ウィザード](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)します。|データベースのパスを選択すると、接続が構成されて、**データ ソース構成ウィザード**します。 詳細については、「 [How to: Connect to Data in a Database](../data-tools/how-to-connect-to-data-in-a-database.md)」を参照してください。|  
|実行、 [TableAdapter 構成ウィザード](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)します。|内で接続を作成、 **TableAdapter 構成ウィザード**します。 詳細については、次を参照してください。[作成し、Tableadapter 構成](../data-tools/create-and-configure-tableadapters.md)します。|  
|実行、 [TableAdapters の編集](../data-tools/editing-tableadapters.md)します。|内で接続を作成、 **TableAdapter クエリ構成ウィザード**します。 詳細については、次を参照してください。[方法: TableAdapter クエリの作成](../data-tools/how-to-create-tableadapter-queries.md)です。|  
|項目をドラッグ、[データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)からフォームに、または[Component Designer](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282)します。|項目をドラッグすると接続オブジェクトが作成、**データ ソース**ウィンドウ、 **Windows フォーム デザイナー**または**Component Designer**します。 詳細については、次を参照してください。 [Visual Studio でのデータ コントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)します。|  
|新しいデータ接続を追加[サーバー エクスプ ローラー/データベース エクスプ ローラー](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d)します。|データ接続**サーバー エクスプ ローラー/データベース エクスプ ローラー**データ ウィザード内の利用可能な接続の一覧に表示されます|  
  
## <a name="connection-strings"></a>接続文字列  
 コンパイルされたアプリケーションまたはアプリケーション構成ファイルに接続文字列を格納できます。 詳細については、次を参照してください。[方法: 接続文字列の編集の保存および](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md)します。  
  
## <a name="connection-information-and-security"></a>接続情報とセキュリティ  
 接続を開くには重要なリソース (データベース) にアクセスする必要があるため、多くの場合、接続の設定や操作にはセキュリティ上の問題があります。  
  
 アプリケーション、およびアプリケーションからデータ ソースへのアクセスを保護する方法は、システムのアーキテクチャによって異なります。 たとえば、Web ベースのアプリケーションでは、通常、ユーザーはインターネット インフォメーション サービス (IIS) に匿名でアクセスできるため、セキュリティ資格情報を提示しません。 この場合、アプリケーションは独自のログオン情報を保持し、特定のユーザー情報ではなくこの情報を使用して接続を開き、データベースにアクセスします。  
  
> [!IMPORTANT]
>  接続文字列の詳細 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 統合セキュリティを使用する方が安全です。 詳細については、「[接続情報の保護](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4)」を参照してください。  
  
 イントラネットまたは多階層アプリケーションでは、Windows、IIS、および SQL Server によって提供される統合セキュリティ オプションを利用できます。 このモデルでは、ローカル ネットワークに対するユーザーの認証資格情報がデータベース リソースへのアクセスにも使用され、明示的なユーザー名やパスワードは接続文字列で使用されません。 通常、アクセス許可はデータベース サーバー コンピューター上でグループを使用して確立されるため、データベースにアクセスする可能性があるすべてのユーザーに対して個別にアクセス許可を設定する必要はありません。 このモデルでは、接続用のログオン情報を格納する必要はなく、接続文字列情報を保護するための追加の手順は必要ありません。  
  
 セキュリティの詳細については、次のトピックを参照してください。  
  
-   [ADO.NET アプリケーションのセキュリティ保護](http://msdn.microsoft.com/library/005a1d43-6ee5-471e-ad98-1d30a44d49d5)  
  
-   [Windows フォームにおけるファイルおよびデータへのより安全なアクセス](http://msdn.microsoft.com/library/3cd3e55b-2f5e-40dd-835d-f50f7ce08967)  
  
## <a name="design-time-connections-in-server-explorerdatabase-explorer"></a>サーバー エクスプローラーまたはデータベース エクスプローラーでのデザイン時接続  
 **サーバー エクスプ ローラー/データベース エクスプ ローラー**データ ソースへのデザイン時接続を作成するための手段を提供します。 これにより、使用可能なデータ ソースの参照、データ ソースに含まれるテーブルや列などの要素に関する情報の表示、データベース要素の編集および作成を行うことができます。  
  
 アプリケーションがで使用できる接続を直接使用しない**サーバー エクスプ ローラー/データベース エクスプ ローラー**します。 これらの接続は、デザイン時にデータベースを操作するために [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] で使用されます。 詳細については、次を参照してください。 [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1)します。  
  
 たとえば、デザイン時に使用できます**サーバー エクスプ ローラー/データベース エクスプ ローラー**データベースへの接続を作成します。 後で、フォームをデザインするときに、データベースを参照、テーブルから列を選択してにドラッグ、[データセット デザイナー](../data-tools/creating-and-editing-typed-datasets.md)します。 これを作成、 [TableAdapter](../data-tools/tableadapter-overview.md)データセットにします。 また、新しく作成された TableAdapter に含まれる新しい接続オブジェクトも作成されます。  
  
 デザイン時接続に関する情報は、特定のプロジェクトやソリューションから独立してローカル コンピューターに格納されます。 そのため、アプリケーションでの作業時にデザイン時の接続が確立されるに表示されます**サーバー エクスプ ローラー/データベース エクスプ ローラー**で作業するたびに[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、先のサーバー間の接続ポイントは使用できます。 詳細については、次を参照してください。[方法: サーバー エクスプ ローラーからデータベースに接続する](http://msdn.microsoft.com/en-us/7c1c3067-0d77-471b-872b-639f9f50db74)します。  
  
 [!INCLUDE[SQLObjectExplorer](../includes/sqlobjectexplorer-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [チュートリアル: データベース (Windows フォーム) 内のデータへの接続](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [ASP.NET データ アクセス コンテンツ マップ](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)