---
title: CRT デバッグ ライブラリの使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e550a5fa705f3c85b3464046cd3c92d96bc47ca
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31467957"
---
# <a name="crt-debug-library-use"></a>CRT デバッグ ライブラリの使用方法
C ランタイム ライブラリには、広範なデバッグ支援機能が用意されています。 CRT デバッグ ライブラリのいずれかを使用するのとリンクする必要があります[/debug](/cpp/build/reference/debug-generate-debug-info)してコンパイル **/MDd**、 **/MTd**、または **/LDd**です。  
  
## <a name="remarks"></a>コメント  
 CRT のデバッグに使用する主な定義とマクロは、CRTDBG.h ヘッダー ファイルに記述されています。  
  
 CRT デバッグ ライブラリ内の関数は、デバッグ情報付きでコンパイルされます ([/Z7、/Zd、/Zi、/ZI (デバッグ情報の形式)](/cpp/build/reference/z7-zi-zi-debug-information-format))、最適化されずです。 渡されるパラメーターを検証するためのアサート ステートメントを含む関数もあり、これらの関数のソース コードは公開されています。 このソース コードを利用すると、CRT 関数をステップ実行して、その関数が正常に動作しているかを確認したり、パラメーターやメモリ状態が不正でないかどうかを検証したりできます。 一部の CRT 技術については権利が保有されており、例外処理、浮動小数点数、その他いくつかのルーチンのソース コードは公開されていません。  
  
 Visual C++ をインストールするときに、C ランタイム ライブラリのソース コードをハード ディスクにインストールするかどうかを選択できます。 ソース コードをインストールしない場合は、CRT 関数をステップ実行するときに CD-ROM が必要になります。  
  
 使用できるさまざまなランタイム ライブラリの詳細については、次を参照してください。 [C ランタイム ライブラリ](/cpp/c-runtime-library/crt-library-features)です。  
  
## <a name="see-also"></a>関連項目  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)   
 [/MD、/MT、/LD (ランタイム ライブラリの使用)](/cpp/build/reference/md-mt-ld-use-run-time-library)