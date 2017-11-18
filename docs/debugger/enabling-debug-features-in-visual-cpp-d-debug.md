---
title: "Visual C でのデバッグ機能 (-/d_debug) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
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
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b762f34df693ac3b5992d0b1e9c2ba4fa6fb8cb8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Visual C++ でのデバッグ機能の使用 (/D_DEBUG)
[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]、シンボルを使用してプログラムをコンパイルするときに、アサーションが有効になっているなどの機能をデバッグ**_DEBUG**定義します。 定義できます**_DEBUG** 2 つの方法のいずれかで。  
  
-   指定**#define _DEBUG を define**ソース コードでまたは  
  
-   指定して、 **/D_DEBUG**コンパイラ オプション。 (これらのウィザードを使用して Visual Studio でプロジェクトを作成する場合**/D_DEBUG**デバッグ構成で自動的に定義されている)。  
  
 ときに**_DEBUG**が定義されている場合、コンパイラはコンパイルで囲まれたコードのセクション**#ifdef _DEBUG**と`#endif`です。  
  
 MFC プログラムのデバッグ構成は、MFC ライブラリのデバッグ バージョンとリンクする必要があります。 MFC ヘッダー ファイルによって決定など、定義済みのシンボルに基づいて正しいバージョンにリンクする MFC ライブラリの**_DEBUG**と**_UNICODE**です。 詳細については、「 [MFC ライブラリのバージョン](/cpp/mfc/mfc-library-versions)します。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)