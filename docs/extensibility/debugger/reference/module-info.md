---
title: "MODULE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_INFO"
helpviewer_keywords: 
  - "MODULE_INFO 構造体"
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# MODULE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

特定のモジュール \(DLLEXEまたはアセンブリ\) について説明します。  
  
## 構文  
  
```cpp#  
typedef struct tagMODULE_INFO {   
   MODULE_INFO_FIELDS dwValidFields;  
   BSTR               m_bstrName;  
   BSTR               m_bstrUrl;  
   BSTR               m_bstrVersion;  
   BSTR               m_bstrDebugMessage;  
   UINT64             m_addrLoadAddress;  
   UINT64             m_addrPreferredLoadAddress;  
   DWORD              m_dwSize;  
   DWORD              m_dwLoadOrder;  
   FILETIME           m_TimeStamp;  
   BSTR               m_bstrUrlSymbolLocation;  
   MODULE_FLAGS       m_dwModuleFlags;  
} MODULE_INFO;  
```  
  
```c#  
public struct MODULE_INFO {   
   public uint     dwValidFields;  
   public string   m_bstrName;  
   public string   m_bstrUrl;  
   public string   m_bstrVersion;  
   public string   m_bstrDebugMessage;  
   public ulong    m_addrLoadAddress;  
   public ulong    m_addrPreferredLoadAddress;  
   public uint     m_dwSize;  
   public uint     m_dwLoadOrder;  
   public FILETIME m_TimeStamp;  
   public string   m_bstrUrlSymbolLocation;  
   public uint     m_dwModuleFlags;  
};  
```  
  
## メンバー  
 dwValidFields  
 どのフィールドを表示するかを指定する [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) の列挙体のフラグの組み合わせ。  
  
 m\_bstrName  
 モジュール名。  
  
 m\_bstrUrl  
 モジュールの URL です。  
  
 m\_bstrVersion  
 モジュールのバージョン。  
  
 m\_bstrDebugMessage  
 モジュールのオプションのメッセージは「シンボルを読み込むことができません」。  
  
 m\_addrLoadAddress  
 モジュールの読み込みアドレス。  
  
 m\_addrPreferredLoadAddress  
 モジュールの高い負荷のアドレス。  
  
 m\_dwSize  
 モジュールのサイズ。  
  
 m\_dwLoadOrder  
 モジュールの読み込み順。  
  
 m\_TimeStamp  
 時間シンボル ファイルの最終変更しました。  
  
 m\_bstrUrlSymbolLocation  
 シンボル ファイルの場所 \(たとえば「。  \\ 」\) モジュールで指定されます。  モジュールにシンボルの検索の開始点として使用されます。  
  
 m\_dwModuleFlags  
 モジュールを説明する [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md) の列挙体のフラグの組み合わせ。  
  
## 解説  
 この構造が表示される [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) のメソッドに渡されます。  
  
 この構造体には\[出力\] ウィンドウに表示されます ENT0ENT の各モジュールに対応します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)