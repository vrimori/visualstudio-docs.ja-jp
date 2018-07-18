---
title: 入れ子プロジェクト |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35d0f4f8906acc08733894d1c24b6d8c2199e1f7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131161"
---
# <a name="nesting-projects"></a>入れ子のプロジェクト
VS パッケージを使用するエンタープライズ アプリケーション開発者が類似した種類のプロジェクトでまとめてグループ化できます便利[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を使用して*プロジェクトの入れ子*です。 たとえば、エンタープライズ テンプレート プロジェクトは、カテゴリにプロジェクトをグループ化の入れ子になったプロジェクトを使用します。 ビジネス ファサード プロジェクトや Web UI プロジェクトの場合は、1 つのカテゴリにグループ化。  
  
 このシナリオでは、開発者が親プロジェクトごとの下でネストできますプロジェクトの数に制限、提供するにはプログラムでの制限が、 この種類のグループ化でも作成できます再帰的で、下にある親のサブプロジェクトであると、子の下位に子後者に子プロジェクトと同じ型のプロジェクトを入れ子にすることができます。  
  
 プロジェクトの入れ子はの組み込みの一部ではなく[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 入れ子を有効にして、子プロジェクト内の入れ子のサブプロジェクトにコードを記述する必要があります。 親プロジェクトは、特別な VSPackage、またはプロジェクトの種類を作成し、プロジェクトの入れ子を実装するために必要なコードが含まれる、独自の GUID に登録されています。  
  
 C# Example.Nested プロジェクト サンプルでは、入れ子になったプロジェクトの例を参照できます。  
  
## <a name="nested-projects-example"></a>入れ子になったプロジェクトの使用例  
 ![プロジェクトのソリューションを入れ子になった](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
入れ子になったプロジェクトの使用例  
  
## <a name="see-also"></a>関連項目  
 [方法: 入れ子になったプロジェクトを実装します。](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [入れ子になったプロジェクトのアンロードと再読み込みに関する考慮事項](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [ウィザードでサポートされる入れ子になったプロジェクト](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [プロジェクトと項目テンプレートの登録](../../extensibility/internals/registering-project-and-item-templates.md)   
 [入れ子になったプロジェクトの処理コマンドの実装](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [入れ子になったプロジェクトに対して、AddItem ダイアログ ボックスのフィルター処理](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)   
 [ウィザード (.Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)