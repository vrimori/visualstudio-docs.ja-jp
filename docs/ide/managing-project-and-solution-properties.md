---
title: "プロジェクトおよびソリューションのプロパティの管理 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 6
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
ms.translationtype: HT
ms.sourcegitcommit: 359e1eb5df8f19774d352ace631802367b6dd8c9
ms.openlocfilehash: 481153e7f3d609c56f313ff5ee9f3f1b511dc5ef
ms.contentlocale: ja-jp
ms.lasthandoff: 07/11/2017

---
# <a name="managing-project-and-solution-properties"></a>プロジェクトおよびソリューションのプロパティの管理
プロジェクトのプロパティでは、コンパイル、デバッグ、テストおよび配置の多くの側面を制御します。 プロジェクトのすべての種類に共通のプロパティや、特定の言語またはプラットフォームに固有のプロパティがあります。 プロジェクトのプロパティにアクセスするには、ソリューション エクスプローラーでプロジェクト ノードを右クリックして [プロパティ] を選択するか、メニュー バーの **[クイック起動]** 検索ボックスでプロパティを入力します。  
  
 ![プロジェクトのコンテキスト メニュー](../ide/media/vs2015_proj_prop_menu.gif "vs2015_proj_prop_menu")  
  
 .NET プロジェクトでは、プロジェクト ツリー自体にプロパティ ノードが含まれる場合もあります。  
  
 ![ソリューション エクスプローラー ツリーの [プロパティ] ノード](../ide/media/vs2015_props_se.png "VS2015_Props_SE")  
  
> [!TIP]
>  ソリューションには少数のプロパティがあり、プロジェクト項目にも少数のプロパティがあります。これらのプロパティは、**プロジェクト デザイナー**ではなく、[[プロパティ] ウィンドウ](../ide/reference/properties-window.md)からアクセスします。  
  
## <a name="project-properties"></a>プロジェクトのプロパティ  
 プロジェクトのプロパティはグループごとに編成され、各グループには専用のプロパティ ページがあります。各ページは、さまざまな言語およびプロジェクトの種類に応じて異なることがあります。  
  
### <a name="c-visual-basic-and-f-projects"></a>C# プロジェクト、Visual Basic プロジェクト、F# プロジェクト  
 C# プロジェクト、Visual Basic プロジェクト、F# プロジェクトでは、プロパティは**プロジェクト デザイナー**で公開されます。 C# の WPF プロジェクトの [ビルド] プロパティ ページを次の図に示します。  
  
 ![Visual Studio プロジェクト デザイナー](../ide/media/vs2015_proppage_build.png "VS2015_PropPage_Build")  
  
 プロジェクト デザイナーのそれぞれのプロパティ ページについては、「[プロジェクト プロパティ リファレンス](../ide/reference/project-properties-reference.md)」を参照してください。  
  
### <a name="c-and-javascript-projects"></a>C++ プロジェクトおよび JavaScript プロジェクト  
 C++ プロジェクトおよび JavaScript プロジェクトには、プロジェクトのプロパティを管理するために別のユーザー インターフェイスが用意されています。 この図は、C++ プロジェクトのプロパティ ページを示しています (JavaScript ページはほぼ同じです)。  
  
 ![Visual C&#43;&#43; プロジェクトのプロパティ](../ide/media/vs2015_projprops_cpp.png "VS2015_ProjProps_cpp")  
  
 C++ プロジェクトのプロパティについては、「[プロジェクトのプロパティの操作](/cpp/ide/working-with-project-properties)」を参照してください。 JavaScript のプロパティの詳細については、「[プロパティ ページ、JavaScript](../ide/reference/property-pages-javascript.md)」を参照してください。  
  
## <a name="solution-properties"></a>ソリューションのプロパティ  
 ソリューションのプロパティにアクセスするには、**ソリューション エクスプローラー**でソリューション ノードを右クリックし、**[プロパティ]** を選択します。 このダイアログでは、デバッグ ビルドまたはリリース ビルド用にプロジェクト構成を設定し、F5 キーを押した時点でのスタートアップ プロジェクトとなるプロジェクトを選択し、コード分析のオプションを設定します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のソリューションおよびプロジェクト](../ide/solutions-and-projects-in-visual-studio.md)

