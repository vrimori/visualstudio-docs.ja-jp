---
title: Idiasymbol::get_targetoffset |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetOffset method
ms.assetid: 7d141223-132a-409c-a5a4-94f97340313c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c044ba749c5fae425fab11cdedecc9eb361fffe3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904844"
---
# <a name="idiasymbolgettargetoffset"></a>IDiaSymbol::get_targetOffset
サンク ターゲットのオフセット セクションを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_targetOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]サンク ターゲット アドレスのオフセットの部分を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)