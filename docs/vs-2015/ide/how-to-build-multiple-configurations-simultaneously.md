---
title: '方法: 複数の構成を同時にビルドする | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa16c4c02f92f71d3288896d56b94a6d570c7dd4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930415"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>方法: 複数の構成を同時にビルドする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**[バッチ ビルド]** ダイアログ ボックスを使用すると、複数、またはすべてのプロジェクト ビルド構成で、ほとんどの種類のプロジェクトを同時にビルドできます。 ただし、次の種類のプロジェクトは、複数のビルド構成で同時にビルドすることはできません。  
  
1. JavaScript を使用して Windows 用にビルドされた [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] アプリ。  
  
2. すべての Visual Basic プロジェクト。  
  
   ビルド構成の詳細については、「[ビルド構成について](../ide/understanding-build-configurations.md)」を参照してください。  
  
### <a name="to-build-a-project-in-multiple-build-configurations"></a>複数のビルド構成でプロジェクトをビルドするには  
  
1.  メニュー バーで、**[ビルド]**、**[バッチ ビルド]** の順に選択します。  
  
2.  **[ビルド]** 列で、プロジェクトをビルドする構成のチェック ボックスをオンにします。  
  
    > [!TIP]
    >  ソリューションのビルド構成を編集または作成するには、メニュー バーで **[ビルド]**、**[構成マネージャー]** の順に選択し、**[構成マネージャー]** ダイアログ ボックスを開きます。 ソリューションのビルド構成の編集後に、ソリューションのプロジェクトのすべてのビルド構成を更新するには、**[バッチ ビルド]** ダイアログ ボックスで **[リビルド]** ボタンを選択します。  
  
3.  指定した構成でプロジェクトをビルドするには、**[ビルド]** または **[リビルド]** ボタンを選択します。  
  
## <a name="see-also"></a>関連項目  
 [方法 : 構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)   
 [ビルド構成について](../ide/understanding-build-configurations.md)   
 [MSBuild での複数のプロジェクトの並行ビルド](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)



