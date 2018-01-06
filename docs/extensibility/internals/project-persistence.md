---
title: "プロジェクトの永続化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d77c307ec7b732ba727b7210b4f4eaacb44584aa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="project-persistence"></a>プロジェクトの永続化
永続化は、プロジェクトの主要な設計の考慮事項です。 ほとんどのプロジェクト ファイルを表すプロジェクト項目を使用します。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]もデータが含まれるファイル ベースのプロジェクトをサポートします。 プロジェクトとプロジェクト ファイルによって所有されている、ファイルの両方を保存する必要があります。 IDE では、プロジェクト自体またはプロジェクト項目を保存するように指示します。  
  
 プロジェクトのテンプレートは、プロジェクト ファクトリに渡されます。 テンプレートには、特定のプロジェクトの種類の要件に従ってすべてのプロジェクト項目の初期化をサポートする必要があります。 これらのテンプレートをプロジェクト ファイルとして保存後でおよびソリューションを通じて、IDE によって管理できます。 詳細については、次を参照してください。[を作成するプロジェクト インスタンスで使用してプロジェクト ファクトリ](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)と[ソリューション](../../extensibility/internals/solutions.md)です。  
  
 プロジェクト項目は、ファイル ベースまたはファイル ベースになります。  
  
-   ファイルベースのアイテムには、ローカルまたはリモートを指定できます。 C# での Web プロジェクトでなど、リモート システム上のファイルへの接続を永続化、ローカル ファイル自体が、リモート システムに保持されします。  
  
-   項目の非ファイル ベースでは、データベースのリポジトリにアイテムを保存できます。  
  
## <a name="commit-models"></a>モデルをコミットします。  
 プロジェクト項目が配置されているかを決定した後は、適切なコミット モデルを選択する必要があります。 たとえば、モデルでは、ファイル ベースのローカル ファイルと、各プロジェクト保存できます自律的にします。 リポジトリのモデルでは、1 つのトランザクションで複数の項目を保存できます。 詳細については、次を参照してください。[プロジェクトの種類の設計に関する決定事項](../../extensibility/internals/project-type-design-decisions.md)です。  
  
 ファイル名拡張子を調べるには、プロジェクト化を実装、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>インターフェイスを実装するオブジェクトのクライアントを有効にする情報を提供する、**名前を付けて保存** ダイアログ ボックス-を埋めるために、**ファイルの種類**ドロップダウン ボックスの一覧し、初期ファイル名拡張子を管理します。  
  
 IDE の呼び出し、`IPersistFileFormat`必要に応じて項目をプロジェクトが、そのプロジェクトを保持するを示すためにプロジェクト上のインターフェイスです。 そのため、オブジェクトには、そのファイルと形式のすべての側面が所有しています。 これには、オブジェクトの形式の名前が含まれます。  
  
 項目が、ファイルではない場合は、の`IPersistFileFormat`はまだ方法以外のファイル ベースの項目は、永続化します。 プロジェクト用の .vbp ファイルなどのファイル[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]のファイルのプロジェクトまたは .vcproj[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]プロジェクトを保存することも必要があります。  
  
 アクション、保存、IDE を調べ、実行中のドキュメント テーブル (RDT) と、階層にコマンドを渡し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>インターフェイスです。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>項目が変更されているかどうかを判断するメソッドを実装します。 アイテムがある場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A>変更された項目を保存するメソッドを実装します。  
  
 メソッド、`IVsPersistHierarchyItem2`インターフェイスを使用して、再読み込みする項目がある場合、項目が再読み込みするかどうかを決定します。 さらに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A>変更された項目が保存されることがなく破棄されるが発生するメソッドを実装することができます。  
  
## <a name="see-also"></a>参照  
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [プロジェクト ファクトリを使用したプロジェクト インスタンスの作成](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)