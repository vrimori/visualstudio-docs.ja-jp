---
title: BP_LOCATION_TYPE |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d84cb1f79a86de5ad9c9865fcea6a0f46171d7b4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909719"
---
# <a name="bplocationtype"></a>BP_LOCATION_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

ブレークポイント要求のブレークポイントの場所の種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 コンテキストとしては、ブレークポイントの場所の種類を指定します。  
  
 BPLT_STRING  
 ブレークポイントの場所の種類を文字列として指定します。  
  
 BPLT_ADDRESS  
 アドレス ブレークポイントの場所の種類を指定します。  
  
 BPLT_RESOLUTION  
 解決方法としては、ブレークポイントの場所の種類を指定します。  
  
 BPLT_CODE_FILE_LINE  
 ソース コードの行として、ブレークポイントの場所の種類を指定します。  
  
 BPLT_CODE_FUNC_OFFSET  
 コードの関数のオフセットとして、ブレークポイントの場所の種類を指定します。  
  
 BPLT_CODE_CONTEXT  
 コードのコンテキストとしては、ブレークポイントの場所の種類を指定します。  
  
 BPLT_CODE_STRING  
 コード文字列としては、ブレークポイントの場所の種類を指定します。  
  
 BPLT_CODE_ADDRESS  
 コードのアドレスとして、ブレークポイントの場所の種類を指定します。  
  
 BPLT_DATA_STRING  
 データの文字列としては、ブレークポイントの場所の種類を指定します。  
  
 BPLT_TYPE_MASK  
 ブレークポイントの種類は、値から抽出できるように、ビット マスクを指定します。  
  
 BPLT_LOCATION_TYPE_MASK  
 ブレークポイントの場所の種類は、値から抽出できるように、ビット マスクを指定します。  
  
## <a name="remarks"></a>Remarks  
 パラメーターとして渡される、 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)メソッド。  
  
 ブレークポイントの場所の種類は、ブレークポイントの種類と場所の種類で構成されます。 つまり、ブレークポイントの場所の種類は、ブレークポイントの種類だけではありません (たとえば、 `BPT_CODE`) または場所の種類 (たとえば、 `BPLT_FILE_LINE`)。 現在サポートされているすべてのブレークポイントの場所の種類の定義済み定数は、この列挙体に含まれる (`BPLT_CODE_FILE_LINE`を通じて`BPLT_DATA_STRING`)。  
  
 `BPT_CODE` `BPT_DATA`のメンバーである、 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)列挙体。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)

