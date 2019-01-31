---
title: '方法: 作成し、プロジェクトの依存関係の削除 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e4ce804664f78bd4ec329f7e4e66008053291c77
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799773"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>方法: プロジェクトの依存関係を作成および削除する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

複数のプロジェクトを含むソリューションをビルドするとき、最初に特定のプロジェクトをビルドし、他のプロジェクトで使われるコードを生成することが必要な場合があります。 別のプロジェクトによって生成された実行可能コードをプロジェクトで使用するとき、コードを生成するプロジェクトは、そのコードを使うプロジェクトのプロジェクトの依存関係と呼ばれます。 このような依存関係は、**[プロジェクトの依存関係]** ダイアログ ボックスで定義できます。  
  
### <a name="to-assign-dependencies-to-projects"></a>プロジェクトに依存関係を割り当てるには  
  
1. ソリューション エクスプローラーでプロジェクトを選択します。  
  
2. **[プロジェクト]** メニューの **[プロジェクトの依存関係]** を選びます。  
  
    **[プロジェクトの依存関係]** ダイアログ ボックスが表示されます。  
  
   > [!NOTE]
   >  **[プロジェクトの依存関係]** オプションは、複数のプロジェクトを含むソリューションでのみ使うことができます。  
  
3. **[依存関係]** タブで、**[プロジェクト]** ドロップダウン メニューからプロジェクトを選びます。  
  
4. **[依存先]** フィールドで、このプロジェクトより先にビルドする必要のある他のプロジェクトのチェック ボックスをオンにします。  
  
   プロジェクトの依存関係を作成するには、先に複数のプロジェクトでソリューションを構成しておく必要があります。  
  
### <a name="to-remove-dependencies-from-projects"></a>プロジェクトから依存関係を削除するには  
  
1.  ソリューション エクスプローラーでプロジェクトを選択します。  
  
2.  **[プロジェクト]** メニューの **[プロジェクトの依存関係]** を選びます。  
  
     **[プロジェクトの依存関係]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]
    >  **[プロジェクトの依存関係]** オプションは、複数のプロジェクトを含むソリューションでのみ使うことができます。  
  
3.  **[依存関係]** タブで、**[プロジェクト]** ドロップダウン メニューからプロジェクトを選びます。  
  
4.  **[依存先]** フィールドで、このプロジェクトの依存関係ではなくなった他のプロジェクトの横にあるチェック ボックスをオフにします。  
  
## <a name="see-also"></a>「  
 [Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [コードのコンパイルとビルド](../ide/compiling-and-building-in-visual-studio.md)   
 [ビルド構成について](../ide/understanding-build-configurations.md)   
 [(NIB) 方法:プロジェクトのプロパティと構成設定を変更します。](http://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
