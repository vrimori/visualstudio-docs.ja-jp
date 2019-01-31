---
title: Idiasourcefile::get_checksumtype |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9bee821a1ecd0179d3ea64e3d1e1f7efca92d64f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928972"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
チェックサム タイプを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]チェックサムの型を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 チェックサム タイプは、チェックサム アルゴリズムに割り当てられる値です。 たとえば、標準の PDB ファイル形式では、次の値のいずれかができます通常。  
  
|チェックサムの種類|CryptoAPI ラベル|説明|  
|-------------------|---------------------|-----------------|  
|0|\<none>|存在するチェックサムがありません。|  
|1|`CALG_MD5`|MD5 ハッシュ アルゴリズムで生成されたチェックサム。|  
|2|`CALG_SHA1`|SHA1 ハッシュ アルゴリズムで生成されたチェックサム。|  
  
 `CryptoAPI`ラベルは、`ALG_ID`列挙体。 ハッシュ アルゴリズムの詳細についてを参照してください、 `CryptoAPI` 、Microsoft の「[!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)]します。  
  
 ソース ファイルの実際のチェックサムのバイト数を取得する呼び出し、 [idiasourcefile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)メソッド。  
  
## <a name="see-also"></a>「  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)