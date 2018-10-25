---
title: Visual C でのデバッグ機能 (-/d_debug) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 772467caf74a381fc2ef5cc74e8e31bf2ff0503c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949618"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Visual C++ でのデバッグ機能の使用 (/D_DEBUG)
[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]、記号でプログラムをコンパイルするときに、アサーションが有効になっているなどのデバッグ機能 **_DEBUG**定義します。 定義できます **_DEBUG** 2 つの方法のいずれかで。  
  
- 指定 **#define _DEBUG**でソース コード、または  
  
- 指定、 **/D_DEBUG**コンパイラ オプション。 (ウィザードを使って Visual Studio でプロジェクトを作成する場合 **/D_DEBUG**デバッグ構成で自動的に定義されます)。  
  
  ときに **_DEBUG**が定義されている場合、コンパイラはコンパイルで囲まれたコードのセクション **#ifdef _DEBUG**と`#endif`します。  
  
  MFC プログラムのデバッグ構成は、MFC ライブラリのデバッグ バージョンとリンクする必要があります。 MFC ヘッダー ファイルを決定など、定義済みのシンボルに基づいて正しいバージョンとリンクする MFC ライブラリの **_DEBUG**と **_UNICODE**します。 詳細については、次を参照してください。 [MFC ライブラリのバージョン](/cpp/mfc/mfc-library-versions)します。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)