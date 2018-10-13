---
title: Idiasourcefile::get_checksumtype |Microsoft Docs
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
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d4fc1528bc7746547b5351ee93a7789e128703c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260287"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

チェックサム タイプを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]チェックサムの型を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 チェックサム タイプは、チェックサム アルゴリズムに割り当てられる値です。 たとえば、標準の PDB ファイル形式では、次の値のいずれかができます通常。  
  
|チェックサムの種類|CryptoAPI ラベル|説明|  
|-------------------|---------------------|-----------------|  
|0|\<なし >|存在するチェックサムがありません。|  
|1|`CALG_MD5`|MD5 ハッシュ アルゴリズムで生成されたチェックサム。|  
|2|`CALG_SHA1`|SHA1 ハッシュ アルゴリズムで生成されたチェックサム。|  
  
 `CryptoAPI`ラベルは、`ALG_ID`列挙体。 ハッシュ アルゴリズムの詳細についてを参照してください、 `CryptoAPI` 、Microsoft の「[!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)]します。  
  
 ソース ファイルの実際のチェックサムのバイト数を取得する呼び出し、 [idiasourcefile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)



