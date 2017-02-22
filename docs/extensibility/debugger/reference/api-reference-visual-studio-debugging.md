---
title: "API リファレンス (Visual Studio のデバッグ) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグの SDK] のデバッグ、API リファレンス"
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# API リファレンス (Visual Studio のデバッグ)
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

参照セクションにはAPIすべての API 要素の構文と使用方法を示しさまざまなコード例が含まれますガイドの概念について説明します。  すべての参照はカテゴリ別にアルファベット順に表示されます。  
  
 次の表にメソッド`HRESULT`から返された共通の値を示します。  
  
|名前|Description|値|  
|--------|-----------------|-------|  
|S\_OK|成功。|0x00000000|  
|E\_UNEXPECTED|予期しないエラー。|0x8000FFFF|  
|E\_NOTIMPL|実装されていません。|0x80004001|  
|E\_OUTOFMEMORY|操作を完了する十分なメモリ。|0x8007000E|  
|E\_INVALIDARG|1 つ以上の引数が無効です。|0x80070057|  
|E\_NOINTERFACE|サポートされるなどのインターフェイスはありません。|0x80004002|  
|E\_POINTER|無効なポインター。|0x80004003|  
|E\_HANDLE|無効なハンドル。|0x80070006|  
|E\_ABORT|中止操作。|0x80004004|  
|E\_FAIL|予期しないエラー。|0x80004005|  
|E\_ACCESSDENIED|一般的なアクセス拒否エラー。|0x80070005|  
  
> [!NOTE]
>  すべてのパラメーターはポインターであることつまりメソッドの戻り `S_OK` でデバッグ [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] が想定される場合パラメーターのポインターで `S_OK` が戻るとされません。  
  
> [!NOTE]
>  無効な場合は `NULL` \[入力\] パラメーターがIDE がクラッシュする可能性があります。  
  
## 参照  
 [インターフェイス](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Visual Studio デバッガーの拡張性](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)