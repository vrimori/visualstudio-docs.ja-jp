---
title: IPerPropertyBrowsing2 インターフェイス 1 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bded7159b72fc8c1ae8408611ce858105e6734da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344034"
---
# <a name="iperpropertybrowsing2-interface-1"></a>IPerPropertyBrowsing2 インターフェイス 1
オブジェクトによって提供されているプロパティ ページの情報は、アクセスします。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`GetDisplayString`|指定したプロパティを説明するテキスト文字列を返します。|  
|`MapPropertyToPage`|指定したプロパティの操作を許可するプロパティ ページの CLSID を返します。|  
|`GetPredefinedStrings`|カウント対象文字列の配列を返します (`LPOLESTR`ポインター)、指定したプロパティが受け入れることができる、指定できる値の説明を一覧表示します。|  
|`SetPredefinedValue`|プロパティの値をトークンで識別される定義済みの値に設定します。 `dwCookie.`|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: dbgprop.h