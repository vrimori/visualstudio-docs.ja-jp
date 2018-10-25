---
title: (Visual Studio のデバッグ) API リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97d5aa6fc92457557493005389d129993d38e099
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839441"
---
# <a name="api-reference-visual-studio-debugging"></a>API 参照 (Visual Studio のデバッグ)
リファレンス セクションには、API、構文と、API のすべての要素の使用法を示すガイドの概念の概要とコード例のアソートメントが含まれています。 すべての参照は、カテゴリでアルファベット順に一覧表示されます。  
  
 次の表は、一般的な`HRESULT`メソッドによって返される値。  
  
|名前|説明|[値]|  
|----------|-----------------|-----------|  
|S_OK|成功。|0x00000000|  
|E_UNEXPECTED|予期しないエラー。|0x8000FFFF|  
|E_NOTIMPL|実装されていません。|0x80004001|  
|E_OUTOFMEMORY|メモリ不足のため、操作を完了できません。|0x8007000E|  
|E_INVALIDARG|1 つまたは複数の引数が無効です。|0x80070057|  
|E_NOINTERFACE|インターフェイスがサポートされています。|0x80004002|  
|E_POINTER|ポインターが無効です。|0x80004003|  
|E_HANDLE|ハンドルが無効です。|0x80070006|  
|E_ABORT|操作が中止されました。|0x80004004|  
|E_FAIL|予期しないエラー。|0x80004005|  
|E_ACCESSDENIED|一般的なアクセス拒否エラーが発生します。|0x80070005|  
  
> [!NOTE]
>  ときに、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]返しますメソッドをデバッグ`S_OK`、パラメーターのポインターが有効なすべては、検証が実施予定がないで out パラメーター ポインターと見なされますと`S_OK`が返されます。  
> 
> [!NOTE]
>  無効なまたは`NULL`[out] パラメーターは IDE のクラッシュを発生可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Visual Studio デバッガーの拡張性](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)