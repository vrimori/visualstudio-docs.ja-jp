---
title: "EncUnavailableReason | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EncUnavailableReason"
helpviewer_keywords: 
  - "EncUnavailableReason 列挙型"
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# EncUnavailableReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`This is for internal use only!` は  **エディット コンティニュ**  が使用できない理由を表します。  
  
## 構文  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```c#  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### パラメーター  
 ENCUN\_NONE  
 エディット コンティニュでは使用できないである理由を特定の理由はありません。  
  
 ENCUN\_INTEROP  
 エディット コンティニュは相互運用呼び出しでは使用できません。  
  
 ENCUN\_SQLCLR  
 エディット コンティニュは共通言語ランタイムが使用する SQL プロシージャ呼び出しでは使用できません。\(CLR\)  
  
 ENCUN\_MINIDUMP  
 ミニダンプの処理中にエディット コンティニュは使用できません。  
  
 ENCUN\_EMBEDDED  
 埋め込みコードを処理するときにエディット コンティニュは使用できません。  
  
 ENCUN\_ATTACH  
 セッションがにアタッチされているためエディット コンティニュは起動できない場合はデバッガーがあります。  
  
 ENCUN\_WIN64  
 64 ビットの Windows コードの処理中にエディット コンティニュは使用できません。  
  
## 解説  
 この列挙体は [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 内部でのみ使用されます。  カスタム ポートの仕入先によって利用されるように [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) と [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) のメソッドは `E_NOTIMPL` を常に返す必要です。  
  
## 必要条件  
 ヘッダー : msdbg.idl  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)