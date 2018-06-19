---
title: Idiasymbol::get_virtualtableshapeid |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualTableShapeId method
ms.assetid: cbee9944-817a-4805-9c08-fac8e0da58b7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 694dddcbfed79a66c27e2069b3fc7aab7ce7c5f0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472270"
---
# <a name="idiasymbolgetvirtualtableshapeid"></a>IDiaSymbol::get_virtualTableShapeId
シンボルの仮想テーブル シェイプのシンボル id を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_virtualTableShapeId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]シンボルの仮想テーブル図形のシンボル ID を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値の`S_FALSE`プロパティが、シンボルを使用できないことを意味します。  
  
## <a name="remarks"></a>コメント  
 識別子は、一意としてすべてのシンボルをマークする DIA SDK によって作成された一意の値です。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)