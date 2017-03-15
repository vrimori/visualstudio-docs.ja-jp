---
title: "方法 : インストルメントされたバイナリを再配置する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.binaries"
helpviewer_keywords: 
  - "バイナリ、インストルメントされた"
  - "インストルメンテーション、インストルメントされたバイナリ"
  - "インストルメントされたバイナリと再配置"
  - "プロファイリング ツール、インストルメントされたバイナリ"
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# 方法 : インストルメントされたバイナリを再配置する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

インストルメンテーション中、プローブはバイナリに挿入され、アプリケーションのパフォーマンスを測定します。 インストルメントされたバイナリの再配置を選ぶと、元のバイナリのコピーがインストルメント化され、指定した場所に配置されます。 このオプションは、プロファイラーによって元のバイナリの名前を変更したくない場合に役立ちます。 バイナリが再配置されない場合は、バイナリの元のバージョンが上書きされます。  
  
 **必要条件**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、[!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]、[!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### インストルメント化されたバイナリを再配置するには  
  
1.  **パフォーマンス エクスプローラー**で、パフォーマンス セッションを右クリックして、**\[プロパティ\]** をクリックします。  
  
2.  **\[プロパティ ページ\]** で、**\[バイナリ\]** プロパティをクリックします。  
  
3.  **\[インストルメントされたバイナリを再配置\]** チェック ボックスを選びます。  
  
4.  インストルメントされたバイナリの場所を指定します。  
  
## 参照  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)