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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 012236c9d3d02f498843f7a185efdd07c6e96a4d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770858"
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



