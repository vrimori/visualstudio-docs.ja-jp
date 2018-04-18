---
title: Dia2dump サンプル |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acec3fa2def0c478c9d94d71a80b89cda6709897
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="dia2dump-sample"></a>Dia2dump サンプル
Dia2dump サンプルでは、Visual Studio と共にインストールされ、Dia2dump.cpp ソース ファイルが含まれています。 コンパイル済みの実行可能ファイルは、コマンドラインから実行し、全体プログラム データベース (.pdb) ファイルの内容を表示します。  
  
### <a name="to-install-the-sample"></a>サンプルをインストールするには  
  
1.  システムが Visual Studio セットアップ開始ページに記載されているすべてのセットアップ要件を満たしていることを確認します。  
  
2.  Visual Studio をインストールして、サンプルは、のすべてのセットアップとインストールの指示に従います。  
  
#### <a name="to-build-the-sample"></a>サンプルをビルドするには  
  
1.  Visual Studio で Dia2dump.sln ファイルを開きます。 (必要に応じて、Visual Studio を最初に使用して Dia2dump プロジェクトをアップグレードします。)  
  
2.  プロジェクト プロパティ ページで、 **C と C++** &#124; **全般** &#124; **追加のインクルード ディレクトリ**プロパティを指定、`..\DIA SDK\include`ディレクトリ。 これにより、コンパイラが dia2.h ファイルを見つけることができます。  
  
3.  **ビルド** メニューのをクリックして**ソリューションのリビルド**です。  
  
4.  Visual Studio を閉じます。  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  コマンド プロンプトを開き、次に入力します。  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Dia2dump.cpp ソース ファイル](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Visual Studio プロジェクトのポート、移行、アップグレード](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)