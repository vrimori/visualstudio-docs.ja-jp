---
title: "デバッグ セッション ダイアログ ボックスの実行可能ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c52d66d0a2e71b96a907fc73b16d42fa13b080bb
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2018
---
# <a name="executable-for-debugging-session-dialog-box"></a>[デバッグ セッションで実行可能] ダイアログ ボックス
このダイアログ ボックスは、ダイナミック リンク ライブラリ (DLL: Dynamic-Link Library) をデバッグするときに、実行可能ファイルが指定されていない場合に表示されます。 Visual Studio では、DLL を直接起動できません。 代わりに、指定した実行可能ファイルが起動されます。 DLL は、実行可能ファイルから呼び出されたときにデバッグできます。  
  
 **実行可能ファイル名**  
 デバッグ中の DLL を呼び出す実行可能ファイルへのパス名を入力します。  
  
 **プロジェクトは、ここで URL アクセス (ATL Server のみ)**  
 ATL Server の DLL をデバッグする場合は、プロジェクトが存在する URL を入力します。  
  
 URL を入力すると、これらの設定がプロジェクトの [プロパティ ページ] に格納されるため、後続のデバッグ セッションで設定を再入力する必要がなくなります。 設定変更が必要な場合は [プロパティ ページ] を開いて値を変更できます。 デバッグ セッションで、実行可能ファイルを指定する方法の詳細については、次を参照してください。 [Dll のデバッグ](../debugger/how-to-debug-from-a-dll-project.md)です。  
  
## <a name="see-also"></a>参照  
 [Visual Studio でのデバッグ](../debugger/index.md)  
 [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)