---
title: "方法 : Visual Basic 開発者設定が適用されたビルド構成を管理する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 782d860d94cd9e7d4967076a5ea0d3fe86b29400
ms.contentlocale: ja-jp
ms.lasthandoff: 05/24/2017

---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>方法 : Visual Basic 開発者設定が適用されたビルド構成を管理する
既定では、すべてのビルド構成の詳細オプションは [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 開発者設定が適用されて非表示になっています。 このトピックでは、これらの設定を手動で有効にする方法について説明します。  
  
## <a name="enabling-advanced-build-configurations"></a>ビルド構成の詳細を有効にする  
 既定では、**[構成マネージャー]** ダイアログ ボックスおよび[プロジェクト デザイナー](..//ide/reference/application-page-project-designer-visual-basic.md)の **[構成]** 一覧と **[プラットフォーム]** 一覧を開くためのオプションは、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 開発者設定によって非表示になっています。  
  
#### <a name="to-enable-advanced-build-configurations"></a>ビルド構成の詳細を有効にするには  
  
1.  **[ツール]** メニューの **[オプション]**をクリックします。  
  
2.  **[プロジェクトおよびソリューション]** を展開し、**[全般]** をクリックします。  
  
    > [!NOTE]
    >  **[全般]** ノードは、**[すべての設定を表示]** オプションがオフになっている場合でも表示されます。 使用可能なすべてのオプションを表示する場合は、**[すべての設定を表示]** をクリックします。  
  
3.  **[ビルド構成の詳細を表示]** をクリックします。  
  
4.  **[OK]** をクリックします。  
  
     **[ビルド]** メニューで **[構成マネージャー]** を使用できるようになり、**[構成]** 一覧と **[プラットフォーム]** 一覧がプロジェクト デザイナーに表示されるようになります。  
  
## <a name="see-also"></a>関連項目  
 [ビルド構成について](../ide/understanding-build-configurations.md)   
 [コードのコンパイルとビルド](../ide/compiling-and-building-in-visual-studio.md)
