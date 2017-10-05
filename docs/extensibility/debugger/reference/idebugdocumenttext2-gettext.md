---
title: "IDebugDocumentText2::GetText |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentText2::GetText
helpviewer_keywords:
- IDebugDocumentText2::GetText
ms.assetid: f8c15a58-da77-473e-a721-7a094e306c63
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: a7e950fbf8667ee85f992ab8406dfdd9d7442555
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="idebugdocumenttext2gettext"></a>IDebugDocumentText2::GetText
ドキュメント内の指定位置からテキストを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetText(   
   TEXT_POSITION pos,  
   ULONG         cMaxChars,  
   WCHAR*        pText,  
   ULONG*        pcNumChars  
);  
```  
  
```csharp  
int GetText(   
   eumn_TEXT_POSITION pos,  
   uint               cMaxChars,  
   IntPtr             pText,  
   out uint           pcNumChars  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pos`  
 [in]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)構造体を取得するテキストの位置を示すです。  
  
 `cMaxChars`  
 [in]取得するテキストの文字の最大数。  
  
 `pText`  
 [入力、出力].目的のテキストを使用して入力をバッファーへのポインター。 このバッファーは、少なくともできる必要があります`cMaxChars`ワイド文字の数。  
  
 `pcNumChars`  
 [out]実際に取得される文字数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="example"></a>例  
 この例では、このメソッドを呼び出す c# からする方法を示します。  
  
```csharp  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace Mynamespace  
{  
    class MyClass  
    {  
         string GetDocumentText(IDebugDocumentText2 pText, TEXT_POSITION pos)  
        {  
             string documentText = string.Empty;  
             if (pText != null)  
             {  
                  uint numLines = 0;  
                  uint numChars = 0;  
                  int hr;  
                  hr = pText.GetSize(ref numLines, ref numChars);  
                  if (ErrorHandler.Succeeded(hr))  
                  {  
                       IntPtr buffer = Marshal.AllocCoTaskMem((int)numChars * sizeof(char));  
                       uint actualChars = 0;  
                       hr = pText.GetText(pos, numChars, buffer, out actualChars);  
                       if (ErrorHandler.Succeeded(hr))  
                       {  
                            documentText = Marshal.PtrToStringUni(buffer, (int)actualChars);  
                       }  
                       Marshal.FreeCoTaskMem(buffer);  
                  }  
              }  
              return documentText;  
         }  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
