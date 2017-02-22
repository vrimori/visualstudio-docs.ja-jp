---
title: "プロジェクトの種類を作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "新しいプロジェクトの種類"
  - "プロジェクト [Visual Studio SDK] の新しいプロジェクトの種類"
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# プロジェクトの種類を作成します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

拡張する [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を新しいプロジェクトの種類を作成します。 新しいプロジェクトの種類を作成するには、いくつかの概念を理解し、いくつかの手順を完了する必要があります。 次のトピックでは、プロジェクトの種類を作成する方法の概要について説明します。  
  
## このセクションの内容  
 [プロジェクトの種類のデザインの決定](../../extensibility/internals/project-type-design-decisions.md)  
 項目とプロジェクト ファイルの永続化と新しいプロジェクトの種類を作成する前に確認する必要があるコミットメント メカニック デザインの決定について説明します。  
  
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)  
 コードの編集しコンパイル、ビルド、デバッグ、およびプロジェクトでアプリケーションの配置のプログラミング タスクをサポートする新しいプロジェクトの種類を作成する手順の概要を示します。  
  
 [プロジェクトのファクトリを使用して、プロジェクトのインスタンスを作成します。](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 提供し、プロジェクト ファクトリを使用して、新しいプロジェクトのインスタンスを作成する方法について説明します。  
  
 [プロジェクトの種類を登録します。](../../extensibility/internals/registering-a-project-type.md)  
 レジストリからを提供するステートメントの既定のパスとデータ、およびテーブルの各ステートメントに対してレジストリ スクリプトからのエントリが含まれたのコード サンプルを提供します。  
  
 [プロジェクトの永続化](../../extensibility/internals/project-persistence.md)  
 使用について説明して `IPersistFileFormat` ファイルとプロジェクトのファイル ベースのオブジェクトの両方を保持します。  
  
 [MSBuild の使用](../../extensibility/internals/using-msbuild.md)  
 プロジェクトの種類が使用できる方法について説明、 [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] から構築できるようにするエンジンを構築 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] とコマンドラインでします。  
  
## 関連項目  
 [シンボル参照のツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 などのツールを表示するコードのアーキテクチャについて説明します **オブジェクト ブラウザー** と **クラス ビュー** ウィンドウです。 インターフェイスおよび VSPackage でのオブジェクト参照の実装に使用されるメソッドについて説明します。  
  
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 プロジェクトを再生するエディターを使用してプロジェクト項目を開いたときに決定する意味については、プロジェクト リソースの操作方法です。  
  
 [Windows インストーラーである Vspackage をインストールします。](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 固有の id、VSPackage をできるようにする方法と、Windows インストーラー パッケージで VSPackage Dll とその他の情報をラップする方法を示しています \(します。MSI ファイル\)、顧客に配置するためです。  
  
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 説明方法 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ビューとアドレスの階層です。  
  
 [Vspackages にあります。](../../extensibility/internals/vspackages.md)  
 VSPackage を拡張するインストール可能な COM オブジェクトの概要、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 環境し、独自の VSPackage を実装する方法について説明します。  
  
 [プロジェクトの種類](../../extensibility/internals/project-types.md)  
 プロジェクトを使用してコードを変更、コンパイルしコードのビルドし実行およびコードをデバッグする方法について説明し、プロジェクトの種類を作成する方法の詳細なトピックへのリンクを提供します。