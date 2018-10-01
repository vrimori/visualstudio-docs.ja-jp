---
title: span::span コンストラクター | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9cd7d787c136f6811fe6bc4c20fe24f736b29e4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539336"
---
# <a name="spanspan-constructor"></a>span::span コンストラクター
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[span::span コンス トラクター](https://docs.microsoft.com/visualstudio/profiling/span-span-constructor)します。  
  
`span` クラスの新しいインスタンスを初期化します。  
  
## <a name="syntax"></a>構文  
  
```  
span(  
   const marker_series& _Series,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `_Series`  
 有効なマーカー シリーズ コンテキスト。  
  
 `_Format`  
 0 個以上の書式項目が混在したテキストを含む複合書式指定文字列。各書式項目は、引数リスト内のオブジェクトに対応します。  
  
 `_Importance`  
 重要度レベル。  
  
 `_Category`  
 カテゴリ。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** cvmarkersobj.h  
  
 **名前空間:** Concurrency::diagnostic
 
 ## <a name="see-also"></a>関連項目
 [span クラス](../profiling/span-class.md)



