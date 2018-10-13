---
title: Idiareadexeatoffsetcallback::readexecutableat |Microsoft Docs
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
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67f71dcb40001fa7fae545e1771e97b4cc707684
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209749"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定した実行可能ファイルから指定したオフセットから始まるバイト数を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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



