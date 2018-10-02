---
title: プロジェクトの永続化 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5c44fde30720fe17f4b9f3a5d679750ccb78ee6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547826"
---
# <a name="project-persistence"></a>プロジェクトの永続化
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロジェクトの永続化](https://docs.microsoft.com/visualstudio/extensibility/internals/project-persistence)します。  
  
永続化は、プロジェクトの主要な設計の考慮事項です。 ほとんどのプロジェクト ファイルを表すプロジェクト項目を使用します。[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]もデータが含まれるファイル ベースのプロジェクトをサポートします。 プロジェクトとプロジェクト ファイルによって所有されている、ファイルの両方を保持する必要があります。 IDE には、プロジェクト自体またはプロジェクト項目を保存するように指示します。  
  
 プロジェクトのテンプレートはプロジェクト ファクトリに渡されます。 テンプレートは、特定のプロジェクトの種類の要件に従ってすべてのプロジェクト項目の初期化をサポートする必要があります。 これらのテンプレートをプロジェクト ファイルとして保存後で、ソリューションで、IDE によって管理されています。 詳細については、次を参照してください。[を作成するプロジェクト インスタンスで使用してプロジェクト ファクトリ](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)と[ソリューション](../../extensibility/internals/solutions.md)します。  
  
 プロジェクト項目には、ファイル ベースまたはファイル ベースを指定できます。  
  
-   ファイルベースのアイテムには、ローカルまたはリモートを指定できます。 、C# では、Web プロジェクトでなど、リモート システム上のファイルへの接続を永続化、ローカルでファイル自体がリモート システムに保持されますが、。  
  
-   ファイル ベース以外の項目は、データベースのリポジトリにアイテムを保存できます。  
  
## <a name="commit-models"></a>モデルをコミットします。  
 プロジェクト項目の場所を決定した後は、適切なコミット モデルを選択する必要があります。 たとえば、ローカル ファイルとファイル ベース モデルでの各プロジェクト保存できます自律的に。 リポジトリのモデルでは、1 つのトランザクションで複数の項目を保存できます。 詳細については、次を参照してください。[プロジェクトの種類の設計に関する決定事項](../../extensibility/internals/project-type-design-decisions.md)します。  
  
 プロジェクトの実装ファイル名拡張子を決定する、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>インターフェイスを実装するオブジェクトのクライアントを有効にする情報を提供する、**名前を付けて保存** ダイアログ ボックス-を埋めるために、**ファイルの種類**ドロップダウンの一覧し、最初のファイル名拡張子を管理します。  
  
 IDE の呼び出し、`IPersistFileFormat`インターフェイスをプロジェクトにそのプロジェクトが保持されることを示すために、プロジェクトの項目に応じて。 そのため、オブジェクトは、そのファイルと形式のすべての側面を所有しています。 これには、オブジェクトの形式の名前が含まれます。  
  
 項目が、ファイルではない場合は、`IPersistFileFormat`はまだどのファイル ベースでない項目が保存されます。 プロジェクトの .vbp ファイルなどのファイル[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]プロジェクトまたは .vcproj ファイル[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]プロジェクトでは、永続化もする必要があります。  
  
 アクションでは、保存、IDE を調べ、実行中の document テーブル (RDT) と、階層にコマンドを渡し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>インターフェイス。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>項目が変更されているかどうかを判断するメソッドを実装します。 アイテムがある場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A>メソッドは、変更された項目を保存します。  
  
 メソッド、`IVsPersistHierarchyItem2`インターフェイスを使用して再読み込みする項目がある場合、項目が再読み込みするかどうかを決定します。 さらに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A>が変更された項目が保存されることがなく破棄されるメソッドを実装することができます。  
  
## <a name="see-also"></a>関連項目  
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [プロジェクト ファクトリを使用したプロジェクト インスタンスの作成](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

