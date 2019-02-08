---
title: エラー :混合モードの x64 プロセスがサポートされるは、Microsoft .NET Framework 4 を使用している場合にのみデバッグ以上 |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 61c92460976ec9b95163b83744ee0b01b6ebc572
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986086"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>エラー :x64 プロセスの混合モード デバッグは、Microsoft .NET Framework 4 以上を使用している場合にのみサポートされます
ネイティブ コードとマネージド コードの混合を 64 プロセスでデバックするには、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Version 4 が必要です。 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Version 4 より前のバージョンを使用した 64 ビット プロセスの混合モード デバッグはサポートされません。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 次のいずれかの操作を実行します。  
  
  - [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を Version 4 にアップグレードします。  
  
  - デバッグのため、32 ビット バージョンのアプリケーションをビルドします。  
  
## <a name="see-also"></a>関連項目
 [Remote Debugging](../debugger/remote-debugging.md)
