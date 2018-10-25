---
title: '方法 : インストルメントされたバイナリを再配置する | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d0ddfb3cd52e212965ebf928bf087519f38b0bf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240982"
---
# <a name="how-to-relocate-instrumented-binaries"></a>方法 : インストルメントされたバイナリを再配置する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

インストルメンテーション中、プローブはバイナリに挿入され、アプリケーションのパフォーマンスを測定します。 インストルメントされたバイナリの再配置を選ぶと、元のバイナリのコピーがインストルメント化され、指定した場所に配置されます。 このオプションは、プロファイラーによって元のバイナリの名前を変更したくない場合に役立ちます。 バイナリが再配置されない場合は、バイナリの元のバージョンが上書きされます。  
  
 **必要条件**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、 [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>インストルメント化されたバイナリを再配置するには  
  
1.  **パフォーマンス エクスプローラー**で、パフォーマンス セッションを右クリックして、 **[プロパティ]** をクリックします。  
  
2.  **[プロパティ ページ]** で、 **[バイナリ]** プロパティをクリックします。  
  
3.  **[インストルメントされたバイナリを再配置]** チェック ボックスを選びます。  
  
4.  インストルメントされたバイナリの場所を指定します。  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)



