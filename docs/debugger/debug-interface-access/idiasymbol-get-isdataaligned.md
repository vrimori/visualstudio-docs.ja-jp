---
title: Idiasymbol::get_isdataaligned |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isDataAligned method
ms.assetid: ddd11a41-6c00-4829-acf4-aa1ace8c21a7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2888ce16c64b12ad846289148412733b18bc2500
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465552"
---
# <a name="idiasymbolgetisdataaligned"></a>IDiaSymbol::get_isDataAligned
ユーザー定義型 (UDT) がいくつかの特定のメモリ境界に配置されたかどうかを指定するフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_isDataAligned(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pFlag`  
 [out]返します`TRUE`UDT がいくつかメモリ境界に配置された場合、それを返します`FALSE`です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値の`S_FALSE`プロパティが、シンボルを使用できないことを意味します。  
  
## <a name="remarks"></a>コメント  
 既定以外のデータの整列の実行可能ファイルがコンパイルされるときに、このプロパティを設定、通常は。 たとえば、Microsoft C コンパイラがコマンド ライン オプションを使用してデータのアラインメントを変更できます/Zp*#* ここで、 *#* バイト値です。  
  
## <a name="requirements"></a>要件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|dia2.h|  
|バージョン:|DIA SDK バージョン 8.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)