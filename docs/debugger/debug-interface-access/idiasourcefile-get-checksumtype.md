---
title: "IDiaSourceFile::get_checksumType | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSourceFile::get_checksumType メソッド"
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

チェックサムの種類を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[出力\] チェックサムの型を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 チェックサムの型はチェックサム アルゴリズムにマップできる値です。  たとえば標準 PDB ファイル形式は通常の値が 1 である可能性があります :  
  
|チェックサムの型|CryptoAPI のラベル|Description|  
|--------------|--------------------|-----------------|  
|0|なし|チェックサムが用意されていません。|  
|1|`CALG_MD5`|MD5 ハッシュ アルゴリズムで生成されたチェックサム。|  
|2|`CALG_SHA1`|SHA1 ハッシュ アルゴリズムで生成されたチェックサム。|  
  
 `CryptoAPI` のラベルは `ALG_ID` の列挙体です。  ハッシュ アルゴリズムの詳細についてはMicrosoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)] の `CryptoAPI` のセクションを参照してください。  
  
 ソース ファイルのチェックサム実際のバイトを取得するには[IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) のメソッドを呼び出します。  
  
## 参照  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)