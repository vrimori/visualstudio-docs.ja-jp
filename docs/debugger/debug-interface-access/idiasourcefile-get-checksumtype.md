---
title: "Idiasourcefile::get_checksumtype |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7f34e840dc6389b721610251c592480afbdda5f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)