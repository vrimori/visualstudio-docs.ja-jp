---
title: ビジュアル デザイナーで型を公開する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28dcc17c74a5b5ef3c9784fafe972beb6f170d90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135975"
---
# <a name="exposing-types-to-visual-designers"></a>ビジュアル デザイナーで型を公開します。
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] クラスと型の定義へのアクセスをビジュアル デザイナーを表示するためにデザイン時に必要です。 クラスは、定義済みの (参照とその依存関係) は、現在のプロジェクトの依存関係の完全なセットが含まれるアセンブリのセットから読み込まれます。 ビジュアルなデザイナーのクラスのアクセスとカスタム ツールによって生成されたファイルで定義されている型に必要もあります。  
  
 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]と[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]プロジェクト システム一時 portable から生成されたクラスと型をアクセスするためのサポートを提供する実行可能ファイル (一時 PEs)。 カスタム ツールによって生成されたすべてのファイルは、型がそれらのアセンブリから読み込まれたし、デザイナーに公開されているように、一時アセンブリにコンパイルできます。 各カスタム ツールの出力が個別の一時 pe コンパイルされ、この一時的なコンパイルの成否が生成されたファイルをコンパイルするかどうかにのみ依存します。 場合でも、全体として、プロジェクトをビルドできません、個々 の一時的な Pe をデザイナーに使用できる可能性があります。  
  
 プロジェクト システムは、これらの変更は、カスタム ツールを実行した結果をカスタム ツールの出力ファイルに変更を追跡するため完全にサポートを提供します。 カスタム ツールを実行するたびに新しい一時 PE が生成され、デザイナーに適切な通知が送信されます。  
  
> [!NOTE]
>  一時プログラム実行可能ファイルの生成ファイルがバック グラウンドであるため、コンパイルが失敗した場合、ユーザーにエラーが報告されません。  
  
 一時 PE サポートを利用するカスタム ツールは、次の規則に従う必要があります。  
  
-   `GeneratesDesignTimeSource` レジストリに 1 に設定する必要があります。  
  
     プログラム実行可能ファイルのコンパイルには、この設定がない場所はありません。  
  
-   生成されたコードは、プロジェクトのグローバル設定と同じ言語でなければなりません。  
  
     要求された拡張機能としてレポートするカスタム ツールに関係なく、一時的な PE がコンパイルされた<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>を`GeneratesDesignTimeSource`がレジストリ内の 1 に設定します。 拡張機能は .vb、.cs、または .jsl; を指定する必要はありません。どの拡張機能があります。  
  
-   カスタム ツールによって生成されたコードが有効である必要があり、時に参照プロジェクト内に存在のセットのみを使用して、独自にコンパイルする必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>の実行が終了します。  
  
     一時 PE がコンパイルされると、コンパイラに指定の唯一のソース ファイルは、カスタム ツールの出力を示します。 そのため、一時 PE を使用するカスタム ツールでは、プロジェクト内の他のファイルとは無関係にコンパイルできる出力ファイルを生成する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [BuildManager オブジェクトの概要](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [単一ファイル ジェネレーターの実装](../../extensibility/internals/implementing-single-file-generators.md)   
 [単一ファイル ジェネレーターの登録](../../extensibility/internals/registering-single-file-generators.md)