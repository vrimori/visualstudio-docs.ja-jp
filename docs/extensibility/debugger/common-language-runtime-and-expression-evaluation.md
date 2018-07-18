---
title: 共通言語ランタイムおよび式の評価 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 370b7963c71b74674c7d323a5fa1c2650d3f08d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108548"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>共通言語ランタイムおよび式の評価
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 コンパイラは、Visual Basic および C# の場合 (c-sharp と発音)、共通言語ランタイム (CLR) を対象とする Microsoft Intermediate Language (MSIL)、後でが生成などは、ネイティブ コードにコンパイルします。 CLR では、結果として得られるコードをデバッグするには、(DE) のデバッグ エンジンを提供します。 独自のプログラミング言語を Visual Studio IDE に統合する場合は、MSIL にコンパイルすることもでき、そのため、独自の DE を記述する必要はありません。 ただし、使用するプログラミング言語のコンテキスト内で式を評価できる式エバリュエーター (EE) を記述する必要があります。  
  
## <a name="discussion"></a>説明  
 コンピューターの言語の式は、一連のデータ オブジェクトとそれらの操作に使用される演算子のセットを生成するために一般的に解析されます。 たとえば、"A B"は、データに、加算演算子 (+) を適用する解析可能性があります式は、"A"と"B"可能性のある別のデータ オブジェクトの結果として得られるオブジェクトです。 データ オブジェクト、演算子、およびその関連性が一連の合計は、ツリーのノードにある演算子と、分岐でのデータ オブジェクトのツリーとしてほとんどの場合、プログラムで表現されます。 ツリー形式に分割されている式は、解析ツリーと呼ばれます。  
  
 式が解析されて、各データ オブジェクトを評価するシンボル プロバイダー (SP) が呼び出されます。 たとえば、"A"には、複数のメソッドは、その質問の両方が定義されている"どの A?" A の値を確認する前に応答する必要があります。 SP によって返される応答は、「5 番目のスタック フレームの 3 番目の項目」のようなもの、または「静的メモリの開始を超える 50 バイトである A は、このメソッドに割り当てられた」です。  
  
 プログラム自体の MSIL を生成する、だけでなく、CLR コンパイラは、プログラム データベース (.pdb) ファイルに書き込まれるわかりにくいのデバッグ情報も生成できます。 独自の言語コンパイラでは、CLR コンパイラと同じ形式でのデバッグ情報を生成、限り、CLR の SP は言語のという名前のデータ オブジェクトを識別できます。 名前付きのデータ オブジェクトを特定したら、EE オブジェクトを使用してバインダーへデータ オブジェクトを関連付ける (またはバインド) にメモリ領域にそのオブジェクトの値を保持します。 デは、取得、またはデータ オブジェクトの新しい値を設定します。  
  
 専用のコンパイラが CLR を呼び出してデバッグ情報を提供できます、`ISymbolWriter`インターフェイス (名前空間での .NET Framework で定義されている`System.Diagnostics.SymbolStore`)。 CLR DE と SP を MSIL にコンパイルし、これらのインターフェイスを使用してデバッグ情報を記述、専用のコンパイラが使用することができます。 これには、独自の言語を Visual Studio IDE に統合することが大幅に簡略化します。  
  
 CLR DE 式を評価する独自の EE を呼び出すときに、DE、SP およびバインダー オブジェクトへのインターフェイスで EE を提供します。 したがって、CLR ベースのデバッグ エンジン手段を書き込む必要があるインターフェイスだけを実装する、適切な式エバリュエーター。バインディングと、処理するシンボルの CLR によって行われます。  
  
## <a name="see-also"></a>関連項目  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)