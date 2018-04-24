---
title: Idiareadexeatoffsetcallback::readexecutableat |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44285e1d0ec0210193f196b5436407d8a0c2ff66
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
指定した実行可能ファイルから指定したオフセットで始まるバイト数を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 fileOffset  
 [in]読み取りを開始する実行可能ファイル内のオフセット。  
  
 cbData  
 [in]読み取るバイト数。  
  
 pcbData  
 [out]読み取られたバイト数を返します。  
  
 データ  
 [入力、出力].ファイルから読み取られたバイトに設定している配列。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、絶対ファイル オフセットを使用して実行可能ファイルからデータのバイト数を読み込む DIA サポート コードによって呼び出されます。 サポートにこのメソッドは、 [idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)