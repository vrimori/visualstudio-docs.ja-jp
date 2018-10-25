---
title: Idiareadexeatoffsetcallback::readexecutableat |Microsoft Docs
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
ms.openlocfilehash: a9f1c1ab49205a299b73837685b3d35b352a855d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837985"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
指定した実行可能ファイルから指定したオフセットから始まるバイト数を読み取ります。  
  
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
 [入力、出力]ファイルから読み取られたバイトに設定している配列。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、ファイルの絶対オフセットを使用する実行可能ファイルからバイトのデータを読み込む DIA サポート コードによって呼び出されます。 サポートにこのメソッドは、 [idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)