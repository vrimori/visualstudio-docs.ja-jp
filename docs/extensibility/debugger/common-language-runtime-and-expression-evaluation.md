---
title: "共通言語ランタイムおよび式の評価 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] の式の評価のデバッグ"
  - "式の評価、および共通言語ランタイム"
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 共通言語ランタイムおよび式の評価
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 コンパイラでは、Visual Basic および C\# の場合 \(C シャープと発音\)、共通言語ランタイム \(CLR\) を対象とする Microsoft 中間言語 \(MSIL\)、後でが生成などは、ネイティブ コードにコンパイルします。 CLR では、結果として得られるコードをデバッグするには、\(DE\) のデバッグ エンジンを提供します。 独自のプログラミング言語を Visual Studio IDE に統合する場合は、MSIL にコンパイル時に選択でき、そのため、独自の DE を記述する必要はありません。 ただし、使用するプログラミング言語のコンテキスト内で式を評価できる式エバリュエーター \(EE\) を記述する必要があります。  
  
## 説明  
 コンピューター言語の式は、一般に、データ オブジェクトのセットと、それらを操作するために使用する演算子のセットを生成する解析されます。 たとえば、"A"と"B"別のデータ オブジェクトの処理が式の"A \+ B"は、データに加算演算子 \(\+\) を適用するために解析可能性がありますがオブジェクトです。 データ オブジェクト、演算子、およびそれらの関連の合計セットは、最も多くの場合、プログラムではツリーのノードにある演算子と、分岐でのデータ オブジェクトのツリーとして表されます。 ツリー形式に分割されている式は、解析ツリーと呼ばれます。  
  
 式が解析されている各データ オブジェクトを評価するシンボル プロバイダー \(SP\) が呼び出されます。 たとえば、"A"には、複数のメソッド、質問の両方が定義されている"どの A?" A の値を確定する前に応答する必要があります。 SP によって返される応答は、「5 番目のスタック フレーム上の 3 番目の項目」のようなもの、または「静的メモリの先頭を越える 50 バイトは、A は、このメソッドに割り当てられた」です。  
  
 MSIL を生成して、プログラム自体、以外では、CLR のコンパイラは、プログラム データベース \(.pdb\) ファイルに書き込まれる非常にわかりやすくのデバッグ情報も生成します。 独自の言語コンパイラは、CLR コンパイラと同じ形式でのデバッグ情報を生成している限り、CLR の SP は言語のという名前のデータ オブジェクトを識別することです。 名前付きのデータ オブジェクトが識別されると、EE は、そのオブジェクトの値を保持するメモリ領域にデータ オブジェクトを関連付けます \(またはバインド\) にバインダー オブジェクトを使用します。 デは、取得、またはデータ オブジェクトの新しい値を設定します。  
  
 独自のコンパイラが CLR を呼び出すことによってデバッグ情報を提供、 `ISymbolWriter` インターフェイス \(名前空間に .NET Framework で定義されている `System.Diagnostics.SymbolStore`\)。 CLR DE と SP を MSIL にコンパイルし、これらのインターフェイスを使用してデバッグ情報を記述、独自のコンパイラが使用することができます。 これには、独自の言語を Visual Studio IDE に統合する大幅に簡略化します。  
  
 CLR DE が式を評価する独自の EE を呼び出すと、DE、SP およびバインダー オブジェクトへのインターフェイスと EE を提供します。 したがって、CLR ベースのデバッグ エンジンの手段を記述する必要があるのみインターフェイスを実装する、適切な式エバリュエーター。バインディングと処理の符号の CLR によって行われます。  
  
## 参照  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)