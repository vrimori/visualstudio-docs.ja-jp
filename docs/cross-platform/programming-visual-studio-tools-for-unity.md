---
title: "Visual Studio Tools for Unity のプログラミング | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 3
---
# Visual Studio Tools for Unity のプログラミング
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このセクションでは Visual Studio Tools for Unity API の使用例を示します。  
  
## 例  
 ここでは、Visual Studio Tools for Unity API の使用方法を示す例をいくつか示します。  
  
### VSTU によって作成されたプロジェクト ファイルのカスタマイズ  
 Visual Studio Tools for Unity は、プロジェクト ファイルの生成時に Unity スタイルのコールバックを提供します。  再生成のたびにプロジェクト ファイルを変更する方法については、「[例: プロジェクト ファイルの生成](../cross-platform/customize-project-files-created-by-vstu.md)」をご覧ください。  
  
### Unity のログ コールバックを VSTU と共有する  
 Visual Studio Tools for Unity では、Unity コンソールを Visual Studio にストリーミングできるよう、Unity にログ コールバックを登録します。  エディターのスクリプトもログ コールバックを Unity に登録すると、VSTU コールバックがそれから影響を受けることがあります。  VSTU と Unity ログ コールバックを共有する方法については、「[例: ログのコールバック](../cross-platform/share-the-unity-log-callback-with-vstu.md)」をご覧ください。