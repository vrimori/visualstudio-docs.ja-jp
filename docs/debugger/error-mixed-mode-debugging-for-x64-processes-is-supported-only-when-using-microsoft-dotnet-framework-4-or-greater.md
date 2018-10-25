---
title: 'エラー: 混合モード デバッグ プロセスがサポートされるは、Microsoft .NET Framework 4 を使用している場合にのみ x64 以上 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b1e7159c67ab104156f2dccd6d89413594ded33c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874411"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>エラー: x64 プロセスの混合モード デバッグは、Microsoft .NET Framework 4 以上を使用している場合にのみサポートされます
ネイティブ コードとマネージド コードの混合を 64 プロセスでデバックするには、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Version 4 が必要です。 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Version 4 より前のバージョンを使用した 64 ビット プロセスの混合モード デバッグはサポートされません。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 次のいずれかの操作を実行します。  
  
  - [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を Version 4 にアップグレードします。  
  
  - デバッグのため、32 ビット バージョンのアプリケーションをビルドします。  
  
## <a name="see-also"></a>関連項目  
 [Remote Debugging](../debugger/remote-debugging.md)