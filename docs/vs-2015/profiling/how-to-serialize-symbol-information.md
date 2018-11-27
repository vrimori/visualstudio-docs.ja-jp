---
title: '方法: シンボル情報をシリアル化する | Microsoft Docs'
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
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f57339f7fc5c7c9e2cd34441daf4c8e42d485cc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802513"
---
# <a name="how-to-serialize-symbol-information"></a>方法: シンボル情報をシリアル化する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

アプリケーションの分析に必要なシンボルをシリアル化できます。 シンボルをシリアル化すると、.vsp ファイルにシンボルが追加されます。 シンボル情報を .vsp ファイルに追加すると、他のユーザーは元のシンボルにアクセスすることなく、パフォーマンス レポートを分析できるようになります。 シンボルがシリアル化されない場合は、元のインストルメント化された .exe ファイルおよび .pdb ファイルで .vsp ファイルを分析する必要があります。  
  
### <a name="to-automatically-serialize-symbol-information"></a>シンボル情報を自動的にシリアル化するには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
     **[オプション]** ダイアログ ボックスが表示されます。  
  
2.  **[パフォーマンス ツール]** をクリックします。  
  
3.  **[全般設定]** で **[シンボル情報を自動的にシリアル化]** を選択します。  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)   
 [方法: Windows シンボル情報を参照する](../profiling/how-to-reference-windows-symbol-information.md)   
 [How to: Save Analyzed Report Files (方法: 分析されたレポート ファイルを保存する)](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556)



