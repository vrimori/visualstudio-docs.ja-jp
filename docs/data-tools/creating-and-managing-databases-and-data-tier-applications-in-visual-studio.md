---
title: データベース プロジェクト、サーバー プロジェクト、および Visual Studio で DAC プロジェクト
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7f3d3f8dc34cf354fd6cb6b6689701dab791132d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942531"
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>データベース プロジェクトと Visual Studio でのデータ層アプリケーション

データベース プロジェクトを使用するには、新しいデータベースを作成する新しいデータ層アプリケーション (Dac) と、既存のデータベースとデータ層アプリケーションを更新します。 データベース プロジェクトと DAC プロジェクトの両方を使用すると、マネージまたはネイティブ コードには、これらの手法を適用することと同じように、データベース開発作業をバージョン管理やプロジェクト管理手法を適用できます。 開発チームで DAC プロジェクト、データベース プロジェクトまたはサーバー プロジェクトを作成し、バージョン管理下にあるデータベースおよびデータベース サーバーへの変更を管理することができます。 チームのメンバーは、作成、ビルド、および分離開発環境、または、サンド ボックスで、チームと共有する前に変更をテストするファイルは確認できます。 コードの品質を確保するために、チームが完了し、運用環境に変更をデプロイする前に、データベースの特定のリリースのすべての変更をステージング環境でテストできます。

データ層アプリケーションでサポートされているデータベース機能の一覧は、次を参照してください。[機能は、データ層アプリケーションでサポートされている](/previous-versions/visualstudio/visual-studio-2010/ee362013(v=vs.100))します。 データ層アプリケーションでサポートされていない、データベース内の機能を使用する場合は、データベースに変更を管理するデータベース プロジェクトを代わりに使用する必要があります。

## <a name="common-high-level-tasks"></a>一般的な高度なタスク

| 高レベルのタスク | 関連する参照先 |
| - | - |
| **データ層アプリケーションの開発の開始:** A DAC がで導入された新しい概念[!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)]の定義を格納している、[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]データベースとサポートしているクライアントとサーバー間または 3 層で使用されるオブジェクトをインスタンス化アプリケーション。 DAC には、テーブルやビュー、ログインなどのエンティティのインスタンスと共になどのデータベース オブジェクトが含まれます。 Visual Studio を使用して DAC プロジェクトを作成、DAC パッケージ ファイルを作成およびデータベース管理者のインスタンスに展開するためにその DAC パッケージ ファイルを送信することができます、[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]データベース エンジン。 | -   [作成とデータ層アプリケーションの管理](http://go.microsoft.com/fwlink/?LinkId=160741)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328) |
| **反復的なデータベース開発を実行する:** チェック アウト、プロジェクトの部分を分離開発環境で更新するようにする場合は、開発者やテスト担当者は、します。 この種の環境を使用すると、チームの他のメンバーの影響を与えずに変更をテストすることができます。 変更が完了した後は、バージョン管理、他のチーム メンバーと、変更を取得できますとビルド、テスト サーバーに配置をどこにファイルを確認します。 | -   [クエリおよびテキスト エディター (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327)<br />-   [TRANSACT-SQL デバッガー](http://go.microsoft.com/fwlink/?LinkId=227324) |
| **結果、および変更のデータベースのスクリプトとオブジェクトのプロトタイプ作成、検証テスト:** を使用することができます、[!INCLUDE[tsql](../data-tools/includes/tsql_md.md)]エディターのいずれかの一般的なタスクを実行します。 | -   [クエリおよびテキスト エディター (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) |

## <a name="see-also"></a>関連項目

- [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)
