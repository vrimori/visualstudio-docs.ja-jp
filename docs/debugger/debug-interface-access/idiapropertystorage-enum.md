---
title: IDiaPropertyStorage::Enum |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ff182c2600a41a0e7c13ed460418e93f88baaed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871642"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
このセット内のプロパティの列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppenum`  
 [out]返します、`IEnumSTATPROPSTG`プロパティの列挙型を表す (Microsoft.VisualStudio.OLE.Interop 名前空間の) 内のオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)