---
title: "DA0029: サポートされていない CLR バージョンです。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.29"
  - "vs.performance.rules.DA0029"
helpviewer_keywords: 
  - "vs.performance.29"
  - "vs.performance.DA0029"
  - "vs.performance.rules.DA0029"
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0029: サポートされていない CLR バージョンです。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0029|  
|分類|プロファイリング ツールの使用|  
|プロファイル方法|コマンド ラインからのプロファイリング|  
|メッセージ|収集時に、サポートされていない CLR バージョンが検出されました。  マネージ シンボルが正しく解決されない可能性があります。|  
|規則の種類|情報|  
  
## 原因  
 プロファイリング ツールでサポートされていない [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] を使用するアプリケーションのプロファイリングを実行しようとしています。  
  
## 規則の説明  
 この警告は、アプリケーション内で実行されるマネージ コードに対するシンボルを、プロファイリング ツールが解決できない場合に発生します。  プロファイリング ツールは、[!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] を実行中のアプリケーションに対するマネージ コード シンボルを解決できません。  
  
## 違反の修正方法  
 なし。