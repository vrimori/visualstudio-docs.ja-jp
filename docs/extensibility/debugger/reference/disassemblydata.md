---
title: "DisassemblyData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DisassemblyData"
helpviewer_keywords: 
  - "DisassemblyData 構造体"
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# DisassemblyData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示する統合開発環境用の 1 種類の構成 \(IDE\) 手順について説明します。  
  
## 構文  
  
```cpp#  
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
  
```c#  
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
  
## メンバー  
 `dwFields`  
 どのフィールドを表示するかを指定する [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) の定数。  
  
 `bstrAddress`  
 開始点 \(通常は関連付けられた関数の先頭からのオフセットとして\) アドレス。  
  
 `bstrCodeBytes`  
 この命令のコード バイト数。  
  
 `bstrOpcode`  
 この命令のオペコード。  
  
 `bstrOperands`  
 この命令のオペランド。  
  
 `bstrSymbol`  
 存在する場合そのアドレス \(パブリック シンボル関連付けられているシンボル名など\) です。  
  
 `uCodeLocationId`  
 この逆アセンブル行のコード位置の識別子。  1 行のコード コンテキストでのアドレスが別のコード コンテキストでのアドレスを超える場合1 番目の逆アセンブルしたコード位置の識別子は2 番目のコード識別子の位置より大きい。  
  
 `posBeg`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) アセンブルのデータが開始されるドキュメントの位置に対応します。  
  
 `posEnd`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) アセンブルのデータが終了ドキュメントの位置に対応します。  
  
 `bstrDocumentUrl`  
 ファイル名として表すことができるテキスト ドキュメントに `bstrDocumentUrl` のフィールドはソースが含まれるファイル名とファイル形式 `file://file 名前`  を使用して入力されます。  
  
 ファイル名として表すことができないテキスト ドキュメントに `bstrDocumentUrl` はドキュメントの一意の識別子でありデバッグ エンジンは[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) のメソッドを実装する必要があります。  
  
 このフィールドはチェックサムに関する追加情報を含めることができます。  詳細については" 解説 " を参照してください。  
  
 `dwByteOffset`  
 バイト数にはコード行の先頭から命令です。  
  
 `dwFlags`  
 どのフラグがアクティブであるかを指定する [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) の定数。  
  
## 解説  
 `DisassemblyData` の各構造体は逆アセンブルの 1 とおりの方法について説明します。  これらの構造体の配列は [読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) のメソッドから返されます。  
  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) の構造はテキスト ベースのドキュメントにのみ使用されます。  この命令のソース・コードの範囲はステートメントまたは行から生成された最初については `dwByteOffset == 0` 場合にのみ表示されます。  
  
 非テキストであるドキュメントではドキュメントのコンテキストをコードから取得できます。`bstrDocumentUrl` のフィールドに NULL 値。  `bstrDocumentUrl` のフィールドが `DisassemblyData` の前の要素の `bstrDocumentUrl` のフィールドと同じ値に `bstrDocumentUrl`null を設定します。  
  
 `dwFlags` のフィールドにフラグを設定 `DF_DOCUMENT_CHECKSUM` がある場合は追加のチェックサム情報は `bstrDocumentUrl` のフィールドが指す文字列に従います。  具体的にはnull 終端文字の後に一つの順に続くチェックサムのバイト数を示す 4 バイトの値にチェックサムのバイトに続いてチェックサム アルゴリズムを識別する GUID に従います。  このフィールドを [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] のエンコードとデコードする方法このトピックの例を参照してください。  
  
## 使用例  
 `bstrDocumentUrl` のフィールドには文字列以外 `DF_DOCUMENT_CHECKSUM` フラグが設定されている場合追加情報を含めることができます。  このエンコードされた文字列を作成し読み込みプロセスは [!INCLUDE[vcprvc](../../../debugger/includes/vcprvc_md.md)] に簡単です。  ただし[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] にもう一つの重要です。  好奇心の高い人向けに次の例では [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] からエンコードされた文字列を作成する 1 とおりの方法と [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] のエンコードされた文字列をデコードする 1 とおりの方法を示します。  
  
```c#  
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
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)