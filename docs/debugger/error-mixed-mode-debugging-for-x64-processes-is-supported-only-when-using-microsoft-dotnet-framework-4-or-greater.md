---
title: 'エラー: 混合モード デバッグ プロセスがサポートされるは、Microsoft .NET Framework 4 を使用する場合にのみ x64 以上 |Microsoft ドキュメント'
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
ms.openlocfilehash: d5550383d1d5882d8824ce2d282b2035882cdcef
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471506"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>エラー: x64 プロセスの混合モード デバッグは、Microsoft .NET Framework 4 以上を使用している場合にのみサポートされます
ネイティブ コードとマネージ コードの混合を 64 プロセスでデバックするには、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Version 4 が必要です。 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Version 4 より前のバージョンを使用した 64 ビット プロセスの混合モード デバッグはサポートされません。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   次のいずれかの操作を実行します。  
  
    -   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を Version 4 にアップグレードします。  
  
    -   デバッグのため、32 ビット バージョンのアプリケーションをビルドします。  
  
## <a name="see-also"></a>関連項目  
 [Remote Debugging](../debugger/remote-debugging.md)