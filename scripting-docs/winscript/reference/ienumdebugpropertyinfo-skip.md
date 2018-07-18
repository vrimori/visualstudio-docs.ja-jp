---
title: IEnumDebugPropertyInfo::Skip |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Skip
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d0f8ff65340edfac1c02e5b7e80b7be3fd257c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727212"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
指定した数のスキップ`DebugPropertyInfo`列挙のシーケンス内の構造体。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]数`DebugPropertyInfo`をスキップする列挙のシーケンス内の構造体。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`通常`S_OK`です。 返します`S_FALSE`場合に、列挙体の末尾に現在の要素ポインターを設定および`celt`列挙子の左の要素の数より大きい。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugPropertyInfo インターフェイス](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo 構造体](../../winscript/reference/debugpropertyinfo-structure.md)