---
title: Visual C と C++ のカスタム ビジュアライザーの互換性
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
ms.assetid: 64af5bed-e38b-420f-b9ce-d64f35100aae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 43ac7f0f5506725103d185e575514e821674eb27
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232191"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C と C++ のカスタム ビジュアライザーの互換性

Visual Studio 2019 以降、Visual C には、そのメモリを消費するコンポーネントをホストするための外部の 64 ビット プロセスを使用する、強化されたデバッガーが含まれています。 この更新プログラムの一環として、新しいデバッガーに対応できるようにする Visual C と C++ の式エバリュエーターに特定の拡張機能を更新する必要があります。

移動してこの外部プロセスの使用量をオフにすることができる場合は、従来の C と C++ EE アドインまたは C と C++ のカスタム ビジュアライザーを使用している現在、**ツール** > **オプション** >  **デバッグ**にしてからオフ**ロード デバッグ記号は、外部プロセス (ネイティブのみ) で**します。 このオプションを選択解除した場合は、IDE (devenv.exe) プロセス内でのメモリ使用量が大幅に増加が発生します。 そのため、大規模なプロジェクトをデバッグする場合は、このデバッグ オプションの互換性を確保する、拡張機能の所有者を使用することをお勧めします。

従来の C と C++ EE アドインまたは C と C++ のカスタム ビジュアライザーの所有者の場合でワーカー プロセスの拡張機能の読み込みを選択の詳細についてを見つけることができます、 [Concord 機能拡張サンプル wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting)します。 検索することも、 [C と C++ のカスタム ビジュアライザー サンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer)します。