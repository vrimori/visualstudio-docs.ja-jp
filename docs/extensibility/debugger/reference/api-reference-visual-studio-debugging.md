---
title: "API リファレンス (Visual Studio のデバッグ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9f6e3110ca4988fcc12e547f3bcd82c1026f3aeb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="api-reference-visual-studio-debugging"></a>API リファレンス (Visual Studio のデバッグ)
参照セクションにには、API、構文と、すべての API 要素の使用方法を示すガイドの概念の概要およびさまざまなコード例が含まれます。 すべての参照は、カテゴリでアルファベット順に一覧表示されます。  
  
 次の表は、一般的な`HRESULT`メソッドによって返される値。  
  
|name|説明|[値]|  
|----------|-----------------|-----------|  
|S_OK|成功。|0x00000000|  
|E_UNEXPECTED|予期しないエラーです。|0x8000FFFF|  
|E_NOTIMPL|実装されていません。|0x80004001|  
|E_OUTOFMEMORY|メモリ不足のため、操作を完了できません。|0x8007000E|  
|E_INVALIDARG|1 つまたは複数の引数が無効です。|0x80070057|  
|E_NOINTERFACE|インターフェイスがサポートされています。|0x80004002|  
|E_POINTER|ポインターが無効です。|0x80004003|  
|E_HANDLE|ハンドルが無効です。|0x80070006|  
|E_ABORT|操作が中止されました。|0x80004004|  
|E_FAIL|予期しないエラーです。|0x80004005|  
|E_ACCESSDENIED|一般的なアクセス拒否エラーが発生します。|0x80070005|  
  
> [!NOTE]
>  ときに、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]メソッドのデバッグを返します`S_OK`、パラメーターのポインターが有効なすべては、検証が実施予定がないで out パラメーターのポインターであると見なされますと`S_OK`が返されます。  
  
> [!NOTE]
>  無効なまたは`NULL`[out] パラメーターがあります、IDE がクラッシュします。  
  
## <a name="see-also"></a>参照  
 [インターフェイス](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Visual Studio デバッガーの拡張性](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)