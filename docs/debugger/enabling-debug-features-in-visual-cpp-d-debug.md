---
title: Visual C でのデバッグ機能 (-/d_debug) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 2c18dfec1f6d1581f926fa24d006b3761c2f6fce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976249"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Visual C++ でのデバッグ機能の使用 (/D_DEBUG)
[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] では、シンボル **_DEBUG** を定義してプログラムをコンパイルすると、アサーションなどのデバッグ機能が有効になります。 **_DEBUG** は、次のいずれかの方法で定義できます。  
  
- ソース コードで **#define _DEBUG** を指定します。または  
  
- **/D_DEBUG** コンパイラ オプションを指定します。 (ウィザードを使用して Visual Studio のプロジェクトを作成した場合は、デバッグ構成で **/D_DEBUG** が自動的に定義されます。)  
  
  **_DEBUG** を定義すると、コンパイラでは **#ifdef _DEBUG** と `#endif` で囲まれたコードのセクションがコンパイルされます。  
  
  MFC プログラムのデバッグ構成は、MFC ライブラリのデバッグ バージョンとリンクする必要があります。 MFC ヘッダー ファイルによって、**_DEBUG** や **_UNICODE** など、定義済みのシンボルに基づいて、リンクする MFC ライブラリの適正なバージョンが決定されます。 詳細については、「[MFC ライブラリのバージョン](/cpp/mfc/mfc-library-versions)」を参照してください。  
  
## <a name="see-also"></a>関連項目
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)
