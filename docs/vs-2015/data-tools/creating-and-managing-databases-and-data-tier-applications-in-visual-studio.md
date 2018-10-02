---
title: 作成して、データベースと Visual Studio でのデータ層アプリケーションの管理 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1ea5370349204765932baed828ffb9c9332b088f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545776"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>作成して、データベースと Visual Studio でのデータ層アプリケーションの管理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[の作成と管理データベースおよびデータ層アプリケーション](https://docs.microsoft.com/visualstudio/data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio)します。  
  
  
重要です]
>  データベース プロジェクトの以前のバージョンに含まれていた[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]で提供されるようになりました[!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)]ツール。 詳細については、次を参照してください。 [SQL Server 開発者ツール](http://go.microsoft.com/fwlink/?LinkId=228126)します。  
  
 データベース プロジェクトを使用するには、新しいデータベースを作成する新しいデータ層アプリケーション (Dac) と、既存のデータベースとデータ層アプリケーションを更新します。 データベース プロジェクトと DAC プロジェクトの両方を使用すると、マネージまたはネイティブ コードには、これらの手法を適用することと同じように、データベース開発作業をバージョン管理やプロジェクト管理手法を適用できます。 作成してデータベースおよびデータベース サーバーへの変更を管理、開発チームが役立つことができます、 *DAC プロジェクト*、*データベース プロジェクト*、または*サーバー プロジェクト*し、バージョン管理します。 チームのメンバーが、構築、しに変更をテストするファイルを確認できますし、*分離開発環境*、またはそれらをチームと共有する前に、サンド ボックス。 コードの品質を確保するために、チームが完了し、運用環境に変更をデプロイする前に、データベースの特定のリリースのすべての変更をステージング環境でテストできます。  
  
 データ層アプリケーションでサポートされているデータベース機能の一覧は、次を参照してください。[機能は、データ層アプリケーションでサポートされている](http://go.microsoft.com/fwlink/?LinkId=164239)、Microsoft web サイト。 データ層アプリケーションでサポートされていない、データベース内の機能を使用する場合は、データベースに変更を管理するデータベース プロジェクトを代わりに使用する必要があります。  
  
## <a name="common-high-level-tasks"></a>一般的な高度なタスク  
  
|高レベルのタスク|関連する参照先|  
|----------------------|------------------------|  
|**データ層アプリケーションの開発の開始:** A DAC がで導入された新しい概念[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)]の定義を格納している、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]データベースとサポートしているクライアントとサーバー間または 3 層で使用されるオブジェクトをインスタンス化アプリケーション。 DAC には、テーブルやビュー、ログインなどのエンティティのインスタンスと共になどのデータベース オブジェクトが含まれます。 使用することができます[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]DAC プロジェクトを作成する DAC パッケージ ファイルを作成しのインスタンスに展開するためのデータベース管理者にその DAC パッケージ ファイルを送信、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]データベース エンジン。|-   [データ層アプリケーションの作成および管理する](http://go.microsoft.com/fwlink/?LinkId=160741)(Microsoft web サイト)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**反復的なデータベース開発を実行する:** チェック アウト、プロジェクトの部分を分離開発環境で更新するようにする場合は、開発者やテスト担当者は、します。 この種の環境を使用すると、チームの他のメンバーの影響を与えずに変更をテストすることができます。 変更が完了した後は、バージョン管理、他のチーム メンバーと、変更を取得できますとビルド、テスト サーバーに配置をどこにファイルを確認します。|-   [クエリおよびテキスト エディター (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft web サイト)<br />-   [TRANSACT-SQL デバッガー](http://go.microsoft.com/fwlink/?LinkId=227324) (Microsoft web サイト)|  
|**結果、および変更のデータベースのスクリプトとオブジェクトのプロトタイプ作成、検証テスト:** を使用することができます、[!INCLUDE[tsql](../includes/tsql-md.md)]エディターのいずれかの一般的なタスクを実行します。|-   [クエリおよびテキスト エディター (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft web サイト)|  
  
## <a name="see-also"></a>関連項目  
 [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)

