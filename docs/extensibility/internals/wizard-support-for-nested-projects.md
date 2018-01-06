---
title: "ウィザードでサポートされる入れ子になったプロジェクト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 757968aabfc256cda37a103d48c8d12f1fc16fa5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wizard-support-for-nested-projects"></a>ウィザードでサポートされる入れ子になったプロジェクト
IDE は、親プロジェクトの入れ子になったプロジェクトを実装できる 2 つのウィザードを実行します。**新しいプロジェクト**ウィザードと**項目の追加**ウィザード。  
  
 ユーザーが開始した場合、**新しいプロジェクト**を選択してウィザード**プロジェクトの追加**をクリックすると、**新しいプロジェクト**[ファイル] メニューまたは選択して**追加**右クリックして**新しいプロジェクト**IDE でソリューション エクスプ ローラーが実行、 **AddProject**コマンドと、親プロジェクトの実装、 **AddProject**コマンドは、テンプレートは、プロジェクト ファイルまたはコンテキスト パラメーターのセットを持つウィザード (.vsz) ファイルにするかを返します。  
  
 同様に、親プロジェクトの実装の**AddItem**ウィザードには、コンテキスト パラメーターの異なるセットを持つ .vsz ファイルが返されます。  
  
 ウィザードの詳細については、次を参照してください。[ウィザード (です。Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)、[コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)と[プロジェクトと項目テンプレートの登録](../../extensibility/internals/registering-project-and-item-templates.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [入れ子になったプロジェクト](../../extensibility/internals/nesting-projects.md)