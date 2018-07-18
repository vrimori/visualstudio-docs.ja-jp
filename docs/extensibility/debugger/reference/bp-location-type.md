---
title: BP_LOCATION_TYPE |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db35e354b2cfbe91b9c6041dc6239d2dfd2531f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108944"
---
# <a name="bplocationtype"></a>BP_LOCATION_TYPE
ブレークポイントの要求のブレークポイントの場所の種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```csharp  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## <a name="members"></a>メンバー  
 BPLT_NONE  
 ブレークポイントの位置を指定しません。  
  
 BPLT_FILE_LINE  
 ファイルの行として、ブレークポイントの場所の種類を指定します。  
  
 BPLT_FUNC_OFFSET  
 関数のオフセットとして、ブレークポイントの場所の種類を指定します。  
  
 BPLT_CONTEXT  
 コンテキストには、ブレークポイントの場所の種類を指定します。  
  
 BPLT_STRING  
 ブレークポイントの場所の種類を文字列として指定します。  
  
 BPLT_ADDRESS  
 アドレスとして、ブレークポイントの場所の種類を指定します。  
  
 BPLT_RESOLUTION  
 解決方法として、ブレークポイントの場所の種類を指定します。  
  
 BPLT_CODE_FILE_LINE  
 ソース コードの行として、ブレークポイントの場所の種類を指定します。  
  
 BPLT_CODE_FUNC_OFFSET  
 コードの関数のオフセットとして、ブレークポイントの場所の種類を指定します。  
  
 BPLT_CODE_CONTEXT  
 コードのコンテキストとしては、ブレークポイントの場所の種類を指定します。  
  
 BPLT_CODE_STRING  
 コードの文字列として、ブレークポイントの場所の種類を指定します。  
  
 BPLT_CODE_ADDRESS  
 コード アドレスとして、ブレークポイントの場所の種類を指定します。  
  
 BPLT_DATA_STRING  
 データの文字列として、ブレークポイントの場所の種類を指定します。  
  
 BPLT_TYPE_MASK  
 ブレークポイントの種類は、値から抽出できるように、ビット マスクを指定します。  
  
 BPLT_LOCATION_TYPE_MASK  
 ブレークポイントの場所の種類は、値から抽出できるように、ビット マスクを指定します。  
  
## <a name="remarks"></a>コメント  
 パラメーターとして渡される、 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)メソッドです。  
  
 ブレークポイントの場所の種類は、ブレークポイントの種類と場所の種類で構成されます。 つまり、ブレークポイントの場所の種類は、ブレークポイントの型だけではないこと (たとえば、 `BPT_CODE`) または場所の種類 (たとえば、 `BPLT_FILE_LINE`)。 この列挙体で現在サポートされているすべてのブレークポイントの場所の種類の定義済みの定数が含まれている (`BPLT_CODE_FILE_LINE`を通じて`BPLT_DATA_STRING`)。  
  
 `BPT_CODE` および`BPT_DATA`のメンバーである、 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)列挙します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)