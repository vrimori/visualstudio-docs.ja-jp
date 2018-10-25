---
title: Idiasymbol::get_symtag |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_symTag method
ms.assetid: 139a35bd-faeb-4878-be72-394dedfbb18f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 346bfe7b0d096a9658e5063d97337349cc6a1a04
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887944"
---
# <a name="idiasymbolgetsymtag"></a>IDiaSymbol::get_symTag
シンボル型の分類子を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_symTag (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]値を返します、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)シンボルの種類の分類子を指定する列挙体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="example"></a>例  
  
```C++  
IDiaSymbol* pType;  
DWORD       tag = 0;  
pType->get_symTag( &tag );  
```  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)