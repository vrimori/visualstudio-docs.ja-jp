---
title: "[呼び出し履歴] ウィンドウの混合コードと不足情報 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "マネージ コード、ステップ実行"
  - "[呼び出し履歴] ウィンドウ、混合モード デバッグ"
  - "[呼び出し履歴] ウィンドウ、トラブルシューティング"
  - "ネイティブ フレーム"
  - "マネージ呼び出し履歴"
  - "混合モード デバッグ、呼び出し履歴"
  - "ステップ実行、マネージ コード外"
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# [呼び出し履歴] ウィンドウの混合コードと不足情報
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

マネージ コードとネイティブ コードの呼び出し履歴には違いがあるため、コードの種類が混在する場合、呼び出し履歴にすべてを表示できるとは限りません。  ネイティブ コードがマネージ コードを呼び出すと、**\[呼び出し履歴\]** ウィンドウで以下の不具合が生じます。  
  
-   マネージ コードのすぐ上にあるネイティブ フレームが、**\[呼び出し履歴\]** ウィンドウに表示されない場合があります。  詳細については、「[方法 : ネイティブ フレームが \[呼び出し履歴\] ウィンドウに見つからないときにマネージ コードからステップ アウトする](../Topic/How%20to:%20Step%20out%20of%20Managed%20Code%20when%20Native%20Frames%20are%20Missing%20from%20the%20Call%20Stack%20Window.md)」を参照してください。  
  
-   デバッガーの外部で起動された混合モード アプリケーションでは、**\[呼び出し履歴\]** ウィンドウにマネージ コードだけが表示され、ネイティブ フレームがまったく表示されない場合があります。  
  
 上の 2 つの不具合はめったに発生しません。  ネイティブ コードによるマネージ コードの呼び出しでは、ほとんどの場合、正しい呼び出し履歴が表示されます。  
  
## 参照  
 [方法 : \[呼び出し履歴\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Call%20Stack%20Window.md)