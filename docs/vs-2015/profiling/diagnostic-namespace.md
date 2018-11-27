---
title: diagnostic 名前空間 | Microsoft Docs
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
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ad88a96f67b09d1bc4dd24df4368e1a2943536f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810118"
---
# <a name="diagnostic-namespace"></a>diagnostic 名前空間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`diagnostics` 名前空間は、コンカレンシー ビジュアライザー マーカーを出力するための機能を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
namespace diagnostic;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="classes"></a>クラス  
  
|名前|説明|  
|----------|-----------------|  
|[marker_series クラス](../profiling/marker-series-class.md)|1 つのプロバイダーによって生成されたイベントのシリアル チャネルを表します。|  
|[span クラス](../profiling/span-class.md)|アプリケーションのフェーズを定義します。|  
  
### <a name="enumerations"></a>列挙  
  
|名前|説明|  
|----------|-----------------|  
|[marker_importance 列挙型](../profiling/marker-importance-enumeration.md)|コンカレンシー ビジュアライザー マーカーの重要度レベルを表します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** cvmarkersobj.h  
  
 **名前空間:** Concurrency  
  
## <a name="see-also"></a>関連項目  
 [コンカレンシー名前空間 (コンカレンシー ビジュアライザー)](../profiling/concurrency-namespace-concurrency-visualizer.md)



