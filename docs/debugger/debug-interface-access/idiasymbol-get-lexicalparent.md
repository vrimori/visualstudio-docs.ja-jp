---
title: Idiasymbol::get_lexicalparent |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lexicalParent method
ms.assetid: 4d119965-33a8-474c-9c64-95c5218c389c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec761202f10f087f440c695d834f80045a0ac331
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864117"
---
# <a name="idiasymbolgetlexicalparent"></a>IDiaSymbol::get_lexicalParent
シンボルの構文の親への参照を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_lexicalParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)シンボルの構文の親を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>Remarks  
 シンボルの構文の親は、外側の関数またはモジュールにです。 たとえば、関数パラメーターまたはローカル変数の構文の親は、関数の構文の親は、モジュールで定義されている、関数自体です。  
  
 親の構文が記載されているように表示される可能なシンボル[シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)