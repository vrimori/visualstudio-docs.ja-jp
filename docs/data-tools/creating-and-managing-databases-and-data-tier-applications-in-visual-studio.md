---
title: データベース プロジェクトと DAC プロジェクト
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d8671c46cf2e88ab5d5797dd7a009ff29b953c4e
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281733"
---
# <a name="database-projects-and-data-tier-applications"></a>データベース プロジェクトとデータ層アプリケーション

データベース プロジェクトを使用するには、新しいデータベースを作成する新しいデータ層アプリケーション (Dac) と、既存のデータベースとデータ層アプリケーションを更新します。 データベース プロジェクトと DAC プロジェクトの両方を使用すると、マネージまたはネイティブ コードには、これらの手法を適用することと同じように、データベース開発作業をバージョン管理やプロジェクト管理手法を適用できます。 開発チームで DAC プロジェクト、データベース プロジェクトまたはサーバー プロジェクトを作成し、バージョン管理下にあるデータベースおよびデータベース サーバーへの変更を管理することができます。 チームのメンバーは、作成、ビルド、および分離開発環境、または、サンド ボックスで、チームと共有する前に変更をテストするファイルは確認できます。 コードの品質を確保するために、チームが完了し、運用環境に変更をデプロイする前に、データベースの特定のリリースのすべての変更をステージング環境でテストできます。

データ層アプリケーションでサポートされているデータベース機能の一覧は、次を参照してください。 [DAC が SQL Server オブジェクトのサポート](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions)します。 データ層アプリケーションでサポートされていない、データベース内の機能を使用する場合は、データベースに変更を管理するデータベース プロジェクトを代わりに使用する必要があります。

## <a name="common-high-level-tasks"></a>一般的な高度なタスク

| 高レベルのタスク | 関連する参照先 |
| - | - |
| **データ層アプリケーションの開発の開始:** データ層アプリケーション (DAC) の概念は SQL Server 2008 で導入されました。 DAC には、SQL Server データベースと、クライアントとサーバー間または 3 層アプリケーションで使用されるサポート対象のインスタンス オブジェクトの定義が含まれています。 DAC には、テーブルやビュー、ログインなどのエンティティのインスタンスと共になどのデータベース オブジェクトが含まれます。 Visual Studio を使用して、DAC プロジェクトを作成、DAC パッケージ ファイルを作成し、DAC パッケージ ファイルを SQL Server データベース エンジンのインスタンスに展開するためのデータベース管理者に送信することができます。 | - [データ層アプリケーション](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **反復的なデータベース開発を実行する:** 開発者がチェック アウト、プロジェクトの部分とを分離開発環境で更新します。 この種の環境を使用すると、チームの他のメンバーの影響を与えずに変更をテストすることができます。 変更が完了した後は、バージョン管理、他のチーム メンバーと、変更を取得できますとビルド、テスト サーバーに配置をどこにファイルを確認します。 | - [プロジェクト指向のオフライン データベース開発 (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [TRANSACT-SQL デバッガー (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **結果、および変更のデータベースのスクリプトとオブジェクトのプロトタイプ作成、検証テスト:** いずれかの一般的なタスクを実行する TRANSACT-SQL エディターを使用することができます。 | - [クエリおよびテキスト エディター (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>関連項目

- [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)