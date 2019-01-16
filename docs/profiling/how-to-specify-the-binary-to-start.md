---
title: '方法: 開始するバイナリを指定する | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c569b9e285e4865b8ef637443acdf6026b0fec9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868470"
---
# <a name="how-to-specify-the-binary-to-start"></a>方法: 開始するバイナリを指定する

DLL などのバイナリをプロファイルするには、**[\<Target> プロパティ ページ]** ダイアログ ボックスに情報を入力する必要があります。 この情報は、DLL プロジェクトの呼び出し元アプリケーションの場所を示します。

1. **パフォーマンス エクスプローラー**で、対象のバイナリを右クリックし、**[プロパティ]** をクリックします。

2. **[プロパティ ページ]** ダイアログ ボックスで、**[起動]** プロパティをクリックします。

3. **[プロジェクト プロパティのオーバーライド]** チェック ボックスを選択します。

4. **[起動する実行可能ファイル]** テキスト ボックスで、ファイルの場所を指定します。

5. **[引数]** テキスト ボックスで、アプリケーションを起動するのに必要な引数を指定します。

6. **[作業ディレクトリ]** テキスト ボックスで、ディレクトリの場所を指定します。

7. **[OK]** をクリックします。

## <a name="see-also"></a>関連項目

[パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)