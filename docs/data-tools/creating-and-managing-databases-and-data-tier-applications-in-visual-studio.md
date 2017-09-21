---
title: "Creating and Managing Databases and Data-tier Applications in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing change, databases"
  - "database features of Visual Studio, managing change"
  - "databases, managing change"
  - "managing change, database servers"
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 37
caps.handback.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating and Managing Databases and Data-tier Applications in Visual Studio
> [!IMPORTANT]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の旧バージョンに含まれるデータベース プロジェクトは [!INCLUDE[sql_Denali_long](../data-tools/includes/sql_denali_long_md.md)] のツールで提供されます。  詳細については、[SQL Server の開発者ツール](http://go.microsoft.com/fwlink/?LinkId=228126)" "を参照してください。  
  
 データベース プロジェクトを使用すると、新しいデータベースや新しいデータ層アプリケーション \(DAC\) を作成したり、既存のデータベースやデータ層アプリケーションを更新したりできます。  データベース プロジェクトでも DAC プロジェクトでも、マネージ コードやネイティブ コードの場合とほぼ同じ方法で、データベース開発作業にバージョン管理やプロジェクト管理の手法を適用できます。  *DAC プロジェクト*、*データベース プロジェクト*、または*サーバー プロジェクト*を作成し、それをバージョン管理することによって、開発チームがデータベースやデータベース サーバーに加えた変更を管理できます。  チームのメンバーは、ファイルをチェックアウトし、サンドボックスと呼ばれる*分離開発環境*でファイルに変更を加え、ビルドし、テストしてから、その変更を他のメンバーと共有できます。  コードの品質を確実に維持できるように、チームがデータベースの特定のリリースに加えたすべての変更をステージング環境で完成させ、テストしたうえで、稼動環境に配置することができます。  
  
 データ層アプリケーションでサポートされるデータベース機能の一覧については、Microsoft Web サイト [データ層アプリケーションでサポートされている機能](http://go.microsoft.com/fwlink/?LinkId=164239) の" "を参照してください。  データ層アプリケーションでサポートされない機能をデータベースで使用する場合は、データベース プロジェクトを使用して、データベースに加える変更を管理する必要があります。  
  
## 共通の概要タスク  
  
|高度なタスク|関連する参照先|  
|------------|-------------|  
|**データ層アプリケーションの開発の開始:** [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] で導入された新しい概念である DAC には、[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] データベースの定義と、クライアント サーバー アプリケーションや 3 階層アプリケーションが使用する、サポートされるインスタンス オブジェクトが含まれています。  DAC には、テーブルやビューなどのデータベース オブジェクトと、ログインなどのインスタンス エンティティが含まれています。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を使用して DAC プロジェクトを作成し、DAC パッケージ ファイルをビルドし、その DAC パッケージ ファイルをデータベース管理者に送って、[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] データベース エンジンのインスタンスに配置してもらうことができます。|-   [データ層アプリケーションの作成と管理](http://go.microsoft.com/fwlink/?LinkId=160741) \(Microsoft Web サイト\)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**反復的なデータベース開発の実行:** 開発者やテスト担当者は、プロジェクトの一部をチェックアウトしてから、分離開発環境でそれらを更新します。  このような環境を使用することで、チームの他のメンバーに影響を及ぼさずに変更をテストできます。  変更が完了したら、ファイルをバージョン管理に戻します。チームの他のメンバーは、バージョン管理からそれらの変更を取得してビルドし、テスト サーバーに配置できます。|-   [クエリ エディターとテキスト エディター \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Microsoft Web サイト\)<br />-   [Transact\-SQL のデバッガー](http://go.microsoft.com/fwlink/?LinkId=227324) \(Microsoft Web サイト\)|  
|**プロトタイプ作成、テスト結果の検証、およびデータベース スクリプトとオブジェクトの変更:** [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] エディターを使用して、これらの一般的なタスクを実行できます。|-   [クエリ エディターとテキスト エディター \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Microsoft Web サイト\)|