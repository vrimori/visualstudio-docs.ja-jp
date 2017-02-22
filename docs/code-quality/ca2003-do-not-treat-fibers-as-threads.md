---
title: "CA2003: ファイバーをスレッドとして扱いません | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
helpviewer_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2003: ファイバーをスレッドとして扱いません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotTreatFibersAsThreads|  
|CheckId|CA2003|  
|分類|Microsoft.Reliability|  
|互換性に影響する変更点|なし|  
  
## 原因  
 マネージ スレッドが Win32 スレッドとして扱われています。  
  
## 規則の説明  
 マネージ スレッドが Win32 スレッドであるとは限りません。  マネージ スレッドはファイバーです。  共通言語ランタイム \(CLR: Common Language Runtime\) は、SQL によって所有される実際のスレッドのコンテキストでマネージ スレッドをファイバーとして実行します。  これらのスレッドは、AppDomains および SQL Server プロセスのデータベースで共有できます。  マネージ スレッド ローカル ストレージの使用は有効ですが、アンマネージ スレッド ローカル ストレージは使用できません。また、コードが現在の OS スレッドで再度実行されるとは限りません。  スレッドのロケールなどの設定を変更しないでください。  ロックを開始するスレッドはロックの終了も実行する必要があるので、CreateCriticalSection または CreateMutex を P\/Invoke 経由で呼び出さないでください。  ファイバーを使用する場合はその必要はないため、Win32 クリティカル セクションおよびミューテックスは SQL では無効になります。  System.Thread マネージ オブジェクトのほとんどの状態を安全に使用できます。  これには、マネージ スレッド ローカル ストレージやスレッドの現在のユーザー インターフェイス \(UI\) カルチャが含まれます。  ただし、モデルのプログラミング上の理由から、SQL を使用するときにスレッドの現在のカルチャを変更できません。変更は新しいアクセス許可によって行われます。  
  
## 違反の修正方法  
 スレッドの使用状況を調べて、状況に応じてコードを変更してください。  
  
## 警告を抑制する状況  
 この規則は抑制しないでください。