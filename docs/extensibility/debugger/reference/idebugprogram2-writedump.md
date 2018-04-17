---
title: IDebugProgram2::WriteDump |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b17d75ace19ac53cbcd229d7c15de573c1ecb8b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
ダンプ ファイルを書き込みます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `DumpType`  
 [in]値、 [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md)例として、short、ダンプの種類を指定する列挙体、または時間の長い。  
  
 `pszDumpUrl`  
 [in]ダンプを記述する URL です。 通常の形式では`file://c:\path\filename.ext`、任意の有効な URL があります。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 プログラム ダンプは、現在のスタック フレーム、スタック自体、プログラム、およびプログラムを所有しているメモリ可能性がありますで実行しているスレッドの一覧に通常含まれます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)