---
title: 自動機能の中断 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c8aee8f4ef46d3621bf569b260d943180abd7ad5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178179"
---
# <a name="automatic-feature-suspension"></a>自動機能の中断
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
場合は、使用可能なシステム メモリを少なくなると、200 MB を以下に、Visual Studio コード エディターで、次のメッセージが表示されます。

 ![完全ソリューション解析を中断する警告テキスト](../code-quality/media/fsa-alert.png "FSA_Alert")

 Visual Studio では、メモリ不足の状態を検出すると、安定性を維持するために特定の高度な機能が自動的に中断します。 高度な機能の中断に関する警告が表示されますし、Visual Studio は引き続き以前と同様に機能が、そのパフォーマンスが若干低下します。

 メモリ不足の状態で、以下の処理が行われます。

-   Visual C# および Visual Basic の完全なソリューション分析は無効です。

-   [ガベージ コレクション](http://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9)Visual c# と Visual Basic (GC) の待機時間の短いモードが無効になっています。

-   Visual Studio のキャッシュがフラッシュされます。

## <a name="improve-visual-studio-performance"></a>Visual Studio のパフォーマンスを向上させる
 ヒントやテクニックが大規模なソリューションまたはメモリ不足の状態を扱うときは、Visual Studio のパフォーマンスを向上させる方法については、次を参照してください。[大規模なソリューションのパフォーマンスに関する考慮事項](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)します。

## <a name="full-solution-analysis-suspended"></a>完全ソリューション解析を中断
 完全ソリューション解析は既定では、Visual Basic を有効になっているし、無効になっている Visual c# 用。 ただし、メモリ不足の状態で完全ソリューション解析が自動的に無効に Visual Basic と Visual c# の両方のオプション ダイアログ ボックスで、設定に関係なく。 ただし、再有効化できます完全ソリューション解析を選択して、**再度有効にする**、情報バーが表示されたら、選択してボタン、**完全ソリューション解析を有効にする**オプション ダイアログ ボックスで、チェック ボックスVisual Studio を再起動しています。 オプション ダイアログ ボックスでは、分析の設定、現在の完全なソリューションが常に表示します。 詳細については、次を参照してください。[方法: 有効にすると、完全なソリューション分析を無効にする](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)します。

## <a name="gc-low-latency-disabled"></a>GC 低待機時間無効になっています
 GC の低待機時間モードを再度有効にするには、するには、Visual Studio を再起動します。  既定では、Visual Studio GC 低待機時間モードを有効にして、入力文字列で GC のすべての操作をブロックしないことを確認するを入力するたびにします。 ただし、メモリ不足の状態では、自動の中断に関する警告を表示する Visual Studio が発生する場合は、そのセッションの GC の低待機時間モードが無効です。 Visual Studio を再起動すると、既定の GC の動作を再び有効にされます。 詳細については、「 <xref:System.Runtime.GCLatencyMode> 」を参照してください。

## <a name="visual-studio-caches-flushed"></a>Visual Studio キャッシュがフラッシュ

Visual Studio のすべてのキャッシュは、すぐに空になりますが、現在の開発セッションを続行するか、または Visual Studio を再起動する場合の再作成が開始されます。 フラッシュされたキャッシュには、次の機能のキャッシュが含まれます。

-   [すべての参照の検索]

-   移動

-   使用して追加します。

さらに、Visual Studio の内部操作のために使用するキャッシュもクリアされます。

> [!NOTE]
> 自動機能の中断に関する警告は、セッション単位ではなく、ソリューションごとに 1 回だけ発生します。 つまり、Visual Basic から Visual c# (またはその逆) に切り替えるメモリ不足の状態別に実行すると、別の自動機能の中断に関する警告を取得可能性があることができます。

## <a name="see-also"></a>関連項目

- [方法: 完全ソリューション分析を有効/無効にする](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [ガベージ コレクションの基礎](http://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [大規模なソリューションのパフォーマンスに関する考慮事項](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)