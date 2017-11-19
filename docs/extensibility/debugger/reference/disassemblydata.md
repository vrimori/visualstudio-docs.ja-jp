---
title: "DisassemblyData |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DisassemblyData
helpviewer_keywords: DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 798ac2d76bb3d9b0bcad2a6dbf7e7aa300030b42
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="disassemblydata"></a>DisassemblyData
表示する、統合開発環境 (IDE) の 1 つの逆アセンブリ命令について説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagDisassemblyData {   
   DISASSEMBLY_STREAM_FIELDS dwFields;  
   BSTR                      bstrAddress;  
   BSTR                      bstrAddressOffset;  
   BSTR                      bstrCodeBytes;  
   BSTR                      bstrOpcode;  
   BSTR                      bstrOperands;  
   BSTR                      bstrSymbol;  
   UINT64                    uCodeLocationId;  
   TEXT_POSITION             posBeg;  
   TEXT_POSITION             posEnd;  
   BSTR                      bstrDocumentUrl;  
   DWORD                     dwByteOffset;  
   DISASSEMBLY_FLAGS         dwFlags;  
} DisassemblyData;  
```  
  
```csharp  
public struct DisassemblyData {   
   public uint          dwFields;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrCodeBytes;  
   public string        bstrOpcode;  
   public string        bstrOperands;  
   public string        bstrSymbol;  
   public ulong         uCodeLocationId;  
   public TEXT_POSITION posBeg;  
   public TEXT_POSITION posEnd;  
   public string        bstrDocumentUrl;  
   public uint          dwByteOffset;  
   public uint          dwFlags;  
};  
```  
  
## <a name="members"></a>メンバー  
 `dwFields`  
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)のどのフィールドが埋められますを指定する定数。  
  
 `bstrAddress`  
 いくつかの開始位置 (通常は、関連付けられた関数の先頭) からのオフセットとしてのアドレス。  
  
 `bstrCodeBytes`  
 この命令のコードのバイト数。  
  
 `bstrOpcode`  
 この命令のオペコードです。  
  
 `bstrOperands`  
 この命令のオペランド。  
  
 `bstrSymbol`  
 シンボル名存在する場合に関連付けられているアドレス (パブリック シンボル、ラベル、およびなど)。  
  
 `uCodeLocationId`  
 この行を逆アセンブルしたコードの場所の識別子。 最初の逆アセンブルしたコードの場所識別子は、2 つ目のコードの場所 id よりも大きい値でも 1 つの行のコード コンテキスト アドレスが、別のコードのコンテキストのアドレスよりも大きい場合は。  
  
 `posBeg`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)の逆アセンブル データ開始位置、ドキュメント内の位置に対応します。  
  
 `posEnd`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)逆アセンブル データが終了するドキュメント内の位置に対応します。  
  
 `bstrDocumentUrl`  
 ファイル名として表すことができるテキスト ドキュメント、`bstrDocumentUrl`フィールドは、ソースがある、ファイル名を使用して、形式を使用して`file://file name`です。  
  
 ファイル名として表現できないテキスト ドキュメント用`bstrDocumentUrl`、ドキュメントの一意の識別子であり、デバッグ エンジンを実装する必要があります、 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)メソッドです。  
  
 このフィールドは、チェックサムに関する追加情報を含めることもできます。 詳細については、「解説」を参照してください。  
  
 `dwByteOffset`  
 命令は、コード行の先頭からのバイト数。  
  
 `dwFlags`  
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)アクティブなフラグを指定する定数。  
  
## <a name="remarks"></a>コメント  
 各`DisassemblyData`構造体には、混合モードの 1 つの命令がについて説明します。 これらの構造体の配列から返される、[読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)メソッドです。  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)テキスト ベースのドキュメントの構造体を使用します。 この命令のソース コードの範囲は、たとえば、ステートメントまたは行から生成された最初の命令に対してのみ入力すると、`dwByteOffset == 0`です。  
  
 ドキュメントは、テキスト以外に、コードからドキュメントのコンテキストを取得できます、`bstrDocumentUrl`フィールドが null 値にする必要があります。 場合、`bstrDocumentUrl`フィールドと同じ、`bstrDocumentUrl`フィールド、以前に`DisassemblyData`配列の要素、し、設定、`bstrDocumentUrl`を null 値にします。  
  
 場合、`dwFlags`フィールドには、`DF_DOCUMENT_CHECKSUM`フラグが設定、追加のチェックサム情報が指す文字列に依存し、`bstrDocumentUrl`フィールドです。 具体的には、null 文字列終端文字の後に存在に依存してチェックサム内のバイト数を示す 4 バイトの値によってさらにその後にさらに、その後に、チェックサムのバイトのチェックサム アルゴリズムを識別する GUID。 エンコードし、デコードでこのフィールドについて、このトピックの例を参照してください[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]です。  
  
## <a name="example"></a>例  
 `bstrDocumentUrl`場合、フィールドは、文字列以外の追加情報を含めることができます、`DF_DOCUMENT_CHECKSUM`フラグが設定されています。 作成して、このエンコードされた文字列を読み取り中のプロセスに単純です[!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]です。 ただし、 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]、これは別の問題です。 ユーザーについては、調べたい、次の例からエンコードされた文字列を作成する方法の 1 つ[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]でエンコードされた文字列をデコードする方法の 1 つと[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]です。  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
    class MyClass  
    {  
        string EncodeData(string documentString,  
                          Guid checksumGuid,  
                          byte[] checksumData)  
        {  
            string returnString = documentString;  
  
            if (checksumGuid == null || checksumData == null)  
            {  
                // Nothing more to do. Just return the string.  
                return returnString;  
            }  
  
            returnString += '\0'; // separating null value  
  
            // Add checksum GUID to string.  
            byte[] guidDataArray  = checksumGuid.ToByteArray();  
            int    guidDataLength = guidDataArray.Length;  
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);  
            }  
            // Copy guid data bytes to string as wide characters.  
            // Assumption: sizeof(char) == 2.  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum count (a 32-bit value).  
            Int32 checksumCount = checksumData.Length;  
            Marshal.StructureToPtr(checksumCount, pBuffer, true);  
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum data.  
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);  
            for (int i = 0; i < checksumCount; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, checksumData[i]);  
            }  
            for (int i = 0; i < checksumCount / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
            Marshal.FreeCoTaskMem(pBuffer);  
  
            return returnString;  
        }  
  
        void DecodeData(    string encodedString,  
                        out string documentString,  
                        out Guid   checksumGuid,  
                        out byte[] checksumData)  
       {  
           documentString = String.Empty;  
           checksumGuid = Guid.Empty;  
           checksumData = null;  
  
           IntPtr pBuffer = Marshal.StringToBSTR(encodedString);  
           if (null != pBuffer)  
           {  
               int bufferOffset = 0;  
  
               // Parse string out.  String is assumed to be Unicode.  
               documentString = Marshal.PtrToStringUni(pBuffer);  
               bufferOffset += (documentString.Length + 1) * sizeof(char);  
  
               // Parse Guid out.  
               // Read guid bytes from buffer and store in temporary  
               // buffer that contains only the guid bytes. Then the  
               // Marshal.PtrToStructure() can work properly.  
               byte[] guidDataArray  = checksumGuid.ToByteArray();  
               int    guidDataLength = guidDataArray.Length;  
               IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);  
               for (int i = 0; i < guidDataLength; i++)  
               {  
                   Marshal.WriteByte(pGuidBuffer, i,  
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
               }  
               bufferOffset += guidDataLength;  
               checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));  
               Marshal.FreeCoTaskMem(pGuidBuffer);  
  
              // Parse out the number of checksum data bytes (always 32-bit value).  
              int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);  
              bufferOffset += sizeof(Int32);  
  
              // Parse out the checksum data.  
              checksumData = new byte[dataCount];  
              for (int i = 0; i < dataCount; i++)  
              {  
                  checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);  
              }  
           }  
       }  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)