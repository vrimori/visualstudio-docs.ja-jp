---
title: Visual Studio Tools for Unity のプログラミング | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d70a2fe335b89d18e31128fa284d44d74130c127
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="programming-visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity のプログラミング
このセクションでは、Visual Studio Tools for Unity API を使用するための例が示されています。

## <a name="examples"></a>使用例
 ここでは、Visual Studio Tools for Unity API の使用方法を示す例をいくつか示します。

### <a name="customize-project-files-created-by-vstu"></a>VSTU によって作成されたプロジェクト ファイルのカスタマイズ
 Visual Studio Tools for Unity は、プロジェクト ファイルの生成時に Unity スタイルのコールバックを提供します。 再生成のたびにプロジェクト ファイルを変更する方法については、「[例: プロジェクト ファイルの生成](../cross-platform/customize-project-files-created-by-vstu.md)」をご覧ください。

### <a name="share-the-unity-log-callback-with-vstu"></a>Unity のログ コールバックを VSTU と共有する
 Visual Studio Tools for Unity では、Unity コンソールを Visual Studio にストリーミングできるよう、Unity にログ コールバックを登録します。 エディターのスクリプトもログ コールバックを Unity に登録すると、VSTU コールバックがそれから影響を受けることがあります。 VSTU と Unity ログ コールバックを共有する方法については、「[例: ログ コールバック](../cross-platform/share-the-unity-log-callback-with-vstu.md)」をご覧ください。
