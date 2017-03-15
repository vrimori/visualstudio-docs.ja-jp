---
title: "方法: 複数の構成を同時にビルドする | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# 方法: 複数の構成を同時にビルドする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**\[バッチ ビルド\]** ダイアログ ボックスを使用すると、複数、またはすべてのプロジェクト ビルド構成で、ほとんどのプロジェクトの種類を同時にビルドできます。  ただし、次の種類のプロジェクトは、複数のビルド構成で同時にビルドすることはできません。  
  
1.  JavaScript を使用して Windows 用にビルドされた [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] アプリ。  
  
2.  すべての Visual Basic プロジェクト。  
  
 ビルド構成の詳細については、「[ビルド構成について](../ide/understanding-build-configurations.md)」を参照してください。  
  
### 複数のビルド構成でプロジェクトをビルドするには  
  
1.  メニュー バーで、**\[ビルド\]**、**\[バッチ ビルド\]** の順に選択します。  
  
2.  **\[ビルド\]** 列で、プロジェクトをビルドする構成のチェック ボックスをオンにします。  
  
    > [!TIP]
    >  ソリューションのビルド構成を編集したり、作成したりするには、メニュー バーで、**\[ビルド\]**、**\[構成マネージャー\]** の順にクリックし、**\[構成マネージャー\]** ダイアログ ボックスを開きます。  ソリューションのビルド構成の編集後に、ソリューションのプロジェクトのすべてのビルド構成を更新するには、**\[バッチ ビルド\]** ダイアログ ボックスで **\[リビルド\]** をクリックします。  
  
3.  指定した構成でプロジェクトをビルドするには、**\[ビルド\]** または **\[リビルド\]** をクリックします。  
  
## 参照  
 [方法 : 構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)   
 [ビルド構成について](../ide/understanding-build-configurations.md)   
 [複数のプロジェクトの並行ビルド](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)