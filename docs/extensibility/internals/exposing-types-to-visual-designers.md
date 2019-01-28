---
title: ビジュアル デザイナーへの型を公開する |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8330ab390a80f882ee8a72f04e70d50e55595752
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986840"
---
# <a name="expose-types-to-visual-designers"></a>ビジュアル デザイナーへの型を公開します。
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ビジュアル デザイナーを表示するためにデザイン時にクラスと型定義へのアクセスが必要です。 クラスは、定義済みの一連の (参照とその依存関係) は、現在のプロジェクトの依存関係の完全なセットを含むアセンブリから読み込まれます。 ビジュアル デザイナーのクラスのアクセスとカスタム ツールによって生成されたファイルで定義されている型に必要もあります。  
  
 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]と[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]プロジェクト システム一時的なポータブルで生成されたクラスと型にアクセスするためのサポートを提供する実行可能ファイル (一時 PEs)。 カスタム ツールによって生成されたすべてのファイルは、型がそれらのアセンブリから読み込まれたし、デザイナーに公開されているように、一時アセンブリにコンパイルできます。 各カスタム ツールの出力は別の一時 PE にコンパイルし、この一時的なコンパイルの成否は、生成されたファイルをコンパイルするかどうかのみに依存します。 全体として、プロジェクトはビルドしない場合でも、個々 の一時的な Pe をデザイナーに使用可能な可能性があります。  
  
 プロジェクト システムは、これらの変更は、カスタム ツールを実行した結果を提供する、カスタム ツールの出力ファイルに変更を追跡する完全なサポートを提供します。 カスタム ツールを実行するたびに新しい一時 PE が生成され、デザイナーに適切な通知が送信されます。  
  
> [!NOTE]
>  一時的なプログラムの実行可能ファイルの生成ファイルがバック グラウンドであるため、コンパイルが失敗した場合、ユーザーにエラーが報告されません。  
  
 一時 PE サポートを活用するカスタム ツールは、次の規則に従う必要があります。  
  
-   **GeneratesDesignTimeSource**レジストリ内の 1 に設定する必要があります。  
  
     プログラム実行可能ファイルのコンパイルには、この設定がない場所はありません。  
  
-   生成されたコードは、グローバル プロジェクト設定と同じ言語でなければなりません。  
  
     要求された拡張機能として、カスタム ツールのレポートに関係なく一時 PE がコンパイルされる<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>される**GeneratesDesignTimeSource**がレジストリ内の 1 に設定します。 拡張機能がある必要はありません *.vb*、 *.cs*、または *.jsl*; 任意の拡張機能であることができます。  
  
-   カスタム ツールによって生成されたコードを有効にする必要があり、時に、プロジェクトに存在する参照のセットのみを使用して、独自にコンパイルする必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>の実行が終了します。  
  
     一時 PE がコンパイルされると、コンパイラに提供される唯一のソース ファイルは、カスタム ツールの出力を示します。 そのため、一時 PE を使用するカスタム ツールは、プロジェクト内の他のファイルとは別にコンパイルできる出力ファイルを生成する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [BuildManager オブジェクトの概要](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [単一ファイル ジェネレーターを実装します。](../../extensibility/internals/implementing-single-file-generators.md)   
 [単一ファイル ジェネレーターを登録します。](../../extensibility/internals/registering-single-file-generators.md)