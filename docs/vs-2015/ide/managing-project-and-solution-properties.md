---
title: プロジェクトおよびソリューションのプロパティの管理 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 43b46fc40da93352c4748662b66df91f0d25802b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290551"
---
# <a name="managing-project-and-solution-properties"></a>プロジェクトおよびソリューションのプロパティの管理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

プロジェクトのプロパティでは、コンパイル、デバッグ、テストおよび配置の多くの側面を制御します。 プロジェクトのすべての種類に共通のプロパティや、特定の言語またはプラットフォームに固有のプロパティがあります。 プロジェクトのプロパティにアクセスするには、ソリューション エクスプローラーでプロジェクト ノードを右クリックして [プロパティ] を選択するか、メニュー バーの **[クイック起動]** 検索ボックスでプロパティを入力します。  
  
 ![プロジェクトのコンテキスト メニュー](../ide/media/vs2015-proj-prop-menu.gif "vs2015_proj_prop_menu")  
  
 .NET プロジェクトでは、プロジェクト ツリー自体にもプロパティ ノードがあります。  
  
 ![ソリューション エクスプローラー ツリーの [プロパティ] ノード](../ide/media/vs2015-props-se.png "VS2015_Props_SE")  
  
> [!TIP]
>  ソリューションには少数のプロパティがあり、プロジェクト項目にも少数のプロパティがあります。これらのプロパティは、**プロジェクト デザイナー**ではなく、[[プロパティ] ウィンドウ](../ide/reference/properties-window.md)からアクセスします。  
  
## <a name="project-properties"></a>プロジェクトのプロパティ  
 プロジェクトのプロパティはグループごとに編成され、各グループには専用のプロパティ ページがあります。各ページは、さまざまな言語およびプロジェクトの種類に応じて異なることがあります。  
  
### <a name="c-and-visual-basic-projects"></a>C# プロジェクトおよび Visual Basic プロジェクト  
 C# プロジェクトおよび Visual Basic プロジェクトでは、プロパティは**プロジェクト デザイナー**で公開されます。 C# の WPF プロジェクトの [ビルド] プロパティ ページを次の図に示します。  
  
 ![Visual Studio プロジェクト デザイナー](../ide/media/vs2015-proppage-build.png "VS2015_PropPage_Build")  
  
 プロジェクト デザイナーのそれぞれのプロパティ ページについては、「[プロジェクト プロパティ リファレンス](../ide/reference/project-properties-reference.md)」を参照してください。  
  
### <a name="c-and-javascript-projects"></a>C++ プロジェクトおよび JavaScript プロジェクト  
 C++ プロジェクトおよび JavaScript プロジェクトには、プロジェクトのプロパティを管理するために別のユーザー インターフェイスが用意されています。 この図は、C++ プロジェクトのプロパティ ページを示しています (JavaScript ページはほぼ同じです)。  
  
 ![Visual C&#43;&#43; プロジェクトのプロパティ](../ide/media/vs2015-projprops-cpp.png "VS2015_ProjProps_cpp")  
  
 C++ プロジェクトのプロパティについては、「[プロジェクトのプロパティの操作](http://msdn.microsoft.com/library/9b0d6f8b-7d4e-4e61-aa75-7d14944816cd)」を参照してください。 JavaScript のプロパティの詳細については、「[プロパティ ページ、JavaScript](../ide/reference/property-pages-javascript.md)」を参照してください。  
  
## <a name="solution-properties"></a>ソリューションのプロパティ  
 ソリューションのプロパティにアクセスするには、**ソリューション エクスプローラー**でソリューション ノードを右クリックし、**[プロパティ]** を選択します。 このダイアログでは、デバッグ ビルドまたはリリース ビルド用にプロジェクト構成を設定し、F5 キーを押した時点でのスタートアップ プロジェクトとなるプロジェクトを選択し、コード分析のオプションを設定します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のソリューションおよびプロジェクト](../ide/solutions-and-projects-in-visual-studio.md)



