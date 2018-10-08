---
title: IDebugProgram2::WriteDump |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8708751820ca70386e6c9927105384eee9a96a15
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545116"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugProgram2::WriteDump](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-writedump)します。  
  
ダンプ ファイルに書き込みます。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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

