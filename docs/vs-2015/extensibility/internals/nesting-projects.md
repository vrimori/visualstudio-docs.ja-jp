---
title: 入れ子になったプロジェクト |Microsoft Docs
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
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 70a454877a5cb7638edaff8263b6505de16ee9c9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538347"
---
# <a name="nesting-projects"></a>入れ子になったプロジェクト
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[入れ子プロジェクト](https://docs.microsoft.com/visualstudio/extensibility/internals/nesting-projects)します。  
  
VS パッケージを使用するエンタープライズ アプリケーション開発者が類似した種類のプロジェクトでまとめてを便利にグループ[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]を使用して*プロジェクトの入れ子*します。 たとえば、エンタープライズ テンプレート プロジェクトは、カテゴリにプロジェクトをグループ化の入れ子になったプロジェクトを使用します。 ビジネス ファサード プロジェクトや Web UI プロジェクトの場合は、1 つのカテゴリにグループ化。  
  
 このシナリオでは、開発者は、各親プロジェクトの下で入れ子にできますプロジェクトの数に制限、開発者が制限をプログラムで提供できます。 この種類のグループ化もできる再帰的で、下に子は、親のサブプロジェクトのサブプロジェクト子場合に子プロジェクトと同じ型のプロジェクトを入れ子にすることができます。  
  
 プロジェクトの入れ子の組み込みの一部でない[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 入れ子を有効にして、子プロジェクト内の入れ子のサブプロジェクトにコードを記述する必要があります。 親プロジェクトは、特別な VSPackage は、またはプロジェクトの種類を作成し、プロジェクトの入れ子の実装に必要なコードが含まれる、独自の GUID に登録されています。  
  
 C# Example.Nested プロジェクト サンプルでは、入れ子になったプロジェクトの例が見つかります。  
  
## <a name="nested-projects-example"></a>入れ子になったプロジェクトの例  
 ![プロジェクトのソリューションを入れ子になった](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
入れ子になったプロジェクトの例  
  
## <a name="see-also"></a>関連項目  
 [方法: 入れ子になったプロジェクトの実装](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [入れ子になったプロジェクトのアンロードと再ロードに関する考慮事項](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [入れ子になったプロジェクト ウィザードのサポート](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [プロジェクトと項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)   
 [入れ子になったプロジェクトの処理コマンドの実装](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [入れ子になったプロジェクトの AddItem ダイアログ ボックスのフィルター処理](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)   
 [ウィザード (.Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)

