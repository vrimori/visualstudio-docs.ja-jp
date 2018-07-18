---
title: はじめに (Debug Interface Access SDK) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1fdfe560f22374c0b46305d096bea32a784babe6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457902"
---
# <a name="getting-started-debug-interface-access-sdk"></a>はじめに (Debug Interface Access SDK)
デバッグ インターフェイス アクセス (DIA) SDK では、説明のドキュメントと DIA API を使用する方法を示すサンプルを提供します。 .Pdb ファイルと .dbg ファイルを開き、そのコンテンツのシンボル、値、属性、アドレス、およびその他のデバッグ情報を検索するカスタム アプリケーションを開発するのに DIA SDK のインターフェイスとメソッドを使用します。 この SDK では、C++ アプリケーションで見られる記号に関連するプロパティの参照テーブルも提供します。  
  
 DIA SDK を使用する最適なには、次のようにについて理解する必要があります。  
  
-   C++ プログラミング言語  
  
-   COM プログラミング  
  
-   Visual Studio 統合開発環境 (IDE) のサンプルをコンパイルするため  
  
 DIA SDK は、通常、Visual Studio と共にインストールし、その既定の場所は *[ドライブ]* \Program Files\Microsoft Visual Studio 9.0\DIA SDK。 インストールの一環として、DIA SDK を実装すると、msdia90.dll は自動的に登録はこれを使用するために必要なすべてを含めるように`dia2.h`プログラムとへのリンクで`diaguids.lib`です。  
  
 ヘッダー: include\dia2.h  
  
 ライブラリ: lib\diaguids.lib  
  
 DLL: bin\msdia80.dll  
  
 IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>このセクションの内容  
 [概要](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 DIA. の基本的なアーキテクチャをレビューします。  
  
 [.Pdb ファイルの照会](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 DIA API を使用して、.pdb ファイルを照会する方法の手順を説明します。  
  
## <a name="see-also"></a>関連項目  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)