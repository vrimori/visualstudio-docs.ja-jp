---
title: "方法: 開始するバイナリを指定する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 94dbedfaa008b83ac45cea9afaa6bac2a254e77e
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-specify-the-binary-to-start"></a>方法 : 開始するバイナリを指定する

DLL などのバイナリをプロファイルするには、**[\<Target> プロパティ ページ]** ダイアログ ボックスに情報を入力する必要があります。 この情報は、DLL プロジェクトの呼び出し元アプリケーションの場所を示します。

1. **パフォーマンス エクスプローラー**で、対象のバイナリを右クリックし、**[プロパティ]** をクリックします。

2. **[プロパティ ページ]** ダイアログ ボックスで、**[起動]** プロパティをクリックします。

3. **[プロジェクト プロパティの上書き]** チェック ボックスを選択します。

4. **[起動する実行可能ファイル]** テキスト ボックスで、ファイルの場所を指定します。

5. **[引数]** テキスト ボックスで、アプリケーションを起動するのに必要な引数を指定します。

6. **[作業ディレクトリ]** テキスト ボックスで、ディレクトリの場所を指定します。

7. **[OK]**をクリックします。

## <a name="see-also"></a>関連項目

[パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)