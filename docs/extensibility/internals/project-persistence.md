---
title: プロジェクトの永続化 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15b605d4beffc85c2ac5e8803d627c13dd4c7d38
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021807"
---
# <a name="project-persistence"></a>プロジェクトの永続化
永続化は、プロジェクトの主要な設計の考慮事項です。 ほとんどのプロジェクト ファイルを表すプロジェクト項目を使用します。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]もデータが含まれるファイル ベースのプロジェクトをサポートします。 プロジェクトとプロジェクト ファイルによって所有されている、ファイルの両方を保持する必要があります。 IDE には、プロジェクト自体またはプロジェクト項目を保存するように指示します。  
  
 プロジェクトのテンプレートはプロジェクト ファクトリに渡されます。 テンプレートは、特定のプロジェクトの種類の要件に従ってすべてのプロジェクト項目の初期化をサポートする必要があります。 これらのテンプレートをプロジェクト ファイルとして保存後で、ソリューションで、IDE によって管理されています。 詳細については、次を参照してください。[を作成するプロジェクト インスタンスで使用してプロジェクト ファクトリ](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)と[ソリューション](../../extensibility/internals/solutions.md)します。  
  
 プロジェクト項目には、ファイル ベースまたはファイル ベースを指定できます。  
  
-   ファイルベースのアイテムには、ローカルまたはリモートを指定できます。 、C# では、Web プロジェクトでなど、リモート システム上のファイルへの接続を永続化、ローカルでファイル自体がリモート システムに保持されますが、。  
  
-   ファイル ベース以外の項目は、データベースのリポジトリにアイテムを保存できます。  
  
## <a name="commit-models"></a>モデルをコミットします。  
 プロジェクト項目の場所を決定した後は、適切なコミット モデルを選択する必要があります。 たとえば、ローカル ファイルとファイル ベース モデルでの各プロジェクト保存できます自律的に。 リポジトリのモデルでは、1 つのトランザクションで複数の項目を保存できます。 詳細については、次を参照してください。[プロジェクトの種類の設計に関する決定事項](../../extensibility/internals/project-type-design-decisions.md)します。  
  
 プロジェクトの実装ファイル名拡張子を決定する、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>インターフェイスを実装するオブジェクトのクライアントを有効にする情報を提供する、**名前を付けて保存** ダイアログ ボックス-を埋めるために、**ファイルの種類**ドロップダウンの一覧し、最初のファイル名拡張子を管理します。  
  
 IDE の呼び出し、`IPersistFileFormat`インターフェイスをプロジェクトにそのプロジェクトが保持されることを示すために、プロジェクトの項目に応じて。 そのため、オブジェクトは、そのファイルと形式のすべての側面を所有しています。 これには、オブジェクトの形式の名前が含まれます。  
  
 項目が、ファイルではない場合は、`IPersistFileFormat`はまだどのファイル ベースでない項目が保存されます。 プロジェクトの .vbp ファイルなどのファイル[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]プロジェクトまたは .vcproj ファイル[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]プロジェクトでは、永続化もする必要があります。  
  
 アクションでは、保存、IDE を調べ、実行中の document テーブル (RDT) と、階層にコマンドを渡し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>インターフェイス。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>項目が変更されているかどうかを判断するメソッドを実装します。 アイテムがある場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A>メソッドは、変更された項目を保存します。  
  
 メソッド、`IVsPersistHierarchyItem2`インターフェイスを使用して再読み込みする項目がある場合、項目が再読み込みするかどうかを決定します。 さらに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A>が変更された項目が保存されることがなく破棄されるメソッドを実装することができます。  
  
## <a name="see-also"></a>関連項目  
 [チェックリスト:新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [プロジェクト ファクトリを使用したプロジェクト インスタンスの作成](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)