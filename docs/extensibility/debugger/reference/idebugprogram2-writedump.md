---
title: IDebugProgram2::WriteDump |Microsoft Docs
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
ms.openlocfilehash: 3d2953b3f30a0d485b58afc04e8ce42158a7537e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905273"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
ダンプ ファイルに書き込みます。  
  
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
 [in]値、 [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md)など、簡単に言えば、ダンプの種類を指定する列挙体または時間の長い。  
  
 `pszDumpUrl`  
 [in]ダンプを記述する URL です。 形式で通常、これは`file://c:\path\filename.ext`、任意の有効な URL があります。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 プログラムのダンプは、現在のスタック フレーム、スタック自体、プログラム、およびプログラムを所有するメモリ可能性がありますで実行されているスレッドの一覧に通常が含まれます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)