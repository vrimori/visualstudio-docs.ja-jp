---
title: 入れ子になったプロジェクト ウィザードのサポート |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fe3bb7b5a97fc0e840a425231765f3d33fb98764
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785899"
---
# <a name="wizard-support-for-nested-projects"></a>入れ子になったプロジェクト向けのウィザード サポート
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IDE の入れ子になったプロジェクトの親プロジェクトを実装できる 2 つのウィザードを実行します。**新しいプロジェクト**ウィザードと**項目の追加**ウィザード。  
  
 ユーザーが開始した場合、**新しいプロジェクト**を選択してウィザード**プロジェクトの追加** をクリック**新しいプロジェクト**ファイル メニューまたは選択して**追加**右クリックして**新しいプロジェクト**ソリューション エクスプ ローラーで、IDE が実行される、 **AddProject**コマンドとの親プロジェクトの実装、 **AddProject**テンプレート プロジェクト ファイル、またはウィザード (.vsz) ファイルを一連のコンテキスト パラメーターを持つか、コマンドを返します。  
  
 同様に、親プロジェクトの実装の**AddItem**ウィザードは、異なる一連のコンテキスト パラメーターを含む .vsz ファイルを返します。  
  
 ウィザードの詳細については、次を参照してください。[ウィザード (します。Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)、[コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)と[プロジェクトと項目テンプレートを登録する](../../extensibility/internals/registering-project-and-item-templates.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [入れ子になったプロジェクト](../../extensibility/internals/nesting-projects.md)

