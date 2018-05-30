---
title: Visual Studio での自動機能中断
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: d75c02bf6b817d03492a15b1f827f94eaaf3e306
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="automatic-feature-suspension"></a>自動機能中断

使用可能なシステム メモリが 200 MB 以下まで少なくなった場合、Visual Studio は次のメッセージをコード エディターに表示します。

![完全ソリューション解析を中断する警告テキスト](../code-quality/media/fsa_alert.png)

Visual Studio では、メモリ不足の状態を検出すると、安定性を維持するために特定の高度な機能が自動的に中断します。 Visual Studio は以前と同様、動作しますが、そのパフォーマンスは低下します。

メモリ不足の状態で、次の操作が実行されます。

- Visual C# および Visual Basic の完全なソリューション分析は無効です。

- [ガベージ コレクション](/dotnet/standard/garbage-collection/index)Visual c# と Visual Basic (GC) の低待機時間モードが無効にします。

- Visual Studio のキャッシュをフラッシュします。

## <a name="improve-visual-studio-performance"></a>Visual Studio のパフォーマンスを向上させる

ヒントとトリックで大規模なソリューションまたはメモリの少ない状況を処理する場合は、Visual Studio のパフォーマンスを向上させる方法は、次を参照してください。[大規模なソリューションのパフォーマンスに関する考慮事項](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)です。

## <a name="full-solution-analysis-suspended"></a>完全ソリューション解析を中断

既定では、完全なソリューション分析は、Visual Basic および無効になっている Visual c# 可能です。 ただし、メモリ不足の状態で完全ソリューション解析を自動的に無効 Visual Basic および Visual C# の場合、両方のオプション ダイアログ ボックスで、設定に関係なくです。 ただしを再度有効にする完全なソリューション分析を選択して、**再度有効にする**、情報バーに表示されたとき を選択してボタン、**完全ソリューション解析を有効にする**オプション ダイアログ ボックスで、チェック ボックスVisual Studio を再起動しています。 オプション ダイアログ ボックスでは、分析の設定が現在、完全なソリューションが常に表示します。 詳細については、次を参照してください。[する方法: 有効化と無効の完全なソリューション分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)です。

## <a name="gc-low-latency-disabled"></a>GC 低待機時間無効になっています

GC 低待機時間モードを再度有効にするには、するには、Visual Studio を再起動します。 既定では、Visual Studio GC 低待機時間モードを有効にして、入力文字列での GC 操作をブロックしないことを確認入力としているときにします。 ただし、メモリ不足の状況によって自動保留警告を表示する Visual Studio は、GC 低待機時間モードはそのセッションで無効です。 既定の GC 動作を再度有効 Visual Studio を再起動します。 詳細については、「<xref:System.Runtime.GCLatencyMode>」を参照してください。

## <a name="visual-studio-caches-flushed"></a>Visual Studio キャッシュがフラッシュ

場合は、現在の開発セッションを続行するか、Visual Studio を再起動すると、Visual Studio のすべてのキャッシュが空になることがすぐが再作成を開始します。 キャッシュのフラッシュは、次の機能のキャッシュを含めます。

- すべての参照を検索します。

- 移動

- Using の追加します。

さらに、Visual Studio の内部操作に使用されるキャッシュもクリアされます。

> [!NOTE]
> 自動機能保留警告は、セッションごとの単位ではなく、ソリューションごとに 1 回だけ発生します。 つまり、Visual Basic から Visual c# (またはその逆) に切り替える別のメモリ不足の状態に実行すると、別の自動機能保留警告を取得可能性のあることができます。

## <a name="see-also"></a>関連項目

- [方法: を有効にして、完全なソリューション分析を無効にします。](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [ガベージ コレクションの基礎](/dotnet/standard/garbage-collection/fundamentals)
- [大規模なソリューションのパフォーマンスに関する考慮事項](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
