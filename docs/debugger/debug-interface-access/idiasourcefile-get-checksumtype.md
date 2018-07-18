---
title: Idiasourcefile::get_checksumtype |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83d1aa687ec7f19df61031d4ff334751ccabaebd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31461932"
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
 [out]チェックサム タイプを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 チェックサム タイプは、チェックサム アルゴリズムに割り当てられる値です。 たとえば、標準の PDB ファイル形式では、次の値のいずれかを持つ通常ことができます。  
  
|チェックサム タイプ|CryptoAPI ラベル|説明|  
|-------------------|---------------------|-----------------|  
|0|\<なし >|チェックサムを表示します。|  
|1|`CALG_MD5`|チェックサム MD5 ハッシュ アルゴリズムを使用して生成します。|  
|2|`CALG_SHA1`|チェックサムは、SHA1 ハッシュ アルゴリズムを使用して生成します。|  
  
 `CryptoAPI`ラベルはからでは、`ALG_ID`列挙します。 ハッシュ アルゴリズムの詳細についてを参照してください、 `CryptoAPI` 、マイクロソフトの「[!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)]です。  
  
 ソース ファイルの実際のチェックサム バイトを取得するを呼び出して、 [idiasourcefile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)