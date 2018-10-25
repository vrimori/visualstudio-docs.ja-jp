---
title: IDiaSession::findInlineFramesByVA |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: df9e68f6-e0a4-4cf6-b11d-61c40351e0cd
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b9036da13c3dfe2e39e3b3166c93f423aff5dc2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825752"
---
# <a name="idiasessionfindinlineframesbyva"></a>IDiaSession::findInlineFramesByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

により、クライアントは、すべての指定した仮想アドレス (VA) にインライン フレームを反復処理する列挙体を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT findInlineFramesByVA (   
   IDiaSymbol*       parent,   ULONGLONG         va,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `parent`  
 [in]`IDiaSymbol`親を表すオブジェクト。  
  
 `va`  
 [in]として、問い合わせください。 アドレスを指定します。  
  
 `ppResult`  
 [out]保持する`IDiaEnumSymbols`取得されるフレームの一覧を含むオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)



