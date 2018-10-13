---
title: ビジュアル デザイナーへの型を公開する |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 401ba1744ad03260140ca29d706f24d699863246
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242009"
---
# <a name="exposing-types-to-visual-designers"></a>ビジュアル デザイナーへのタイプの公開
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ビジュアル デザイナーを表示するためにデザイン時にクラスと型定義へのアクセスが必要です。 クラスは、定義済みの一連の (参照とその依存関係) は、現在のプロジェクトの依存関係の完全なセットを含むアセンブリから読み込まれます。 ビジュアル デザイナーのクラスのアクセスとカスタム ツールによって生成されたファイルで定義されている型に必要もあります。  
  
 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]と[!INCLUDE[csprcs](../../includes/csprcs-md.md)]プロジェクト システム一時的なポータブルで生成されたクラスと型にアクセスするためのサポートを提供する実行可能ファイル (一時 PEs)。 カスタム ツールによって生成されたすべてのファイルは、型がそれらのアセンブリから読み込まれたし、デザイナーに公開されているように、一時アセンブリにコンパイルできます。 各カスタム ツールの出力は別の一時 PE にコンパイルし、この一時的なコンパイルの成否は、生成されたファイルをコンパイルするかどうかのみに依存します。 全体として、プロジェクトはビルドしない場合でも個別の一時的な Pe をデザイナーに使用できる可能性があります。  
  
 プロジェクト システムは、これらの変更は、カスタム ツールを実行した結果を提供する、カスタム ツールの出力ファイルに変更を追跡する完全なサポートを提供します。 カスタム ツールを実行するたびに新しい一時 PE が生成され、デザイナーに適切な通知が送信されます。  
  
> [!NOTE]
>  一時的なプログラムの実行可能ファイルの生成ファイルがバック グラウンドであるため、コンパイルが失敗した場合、ユーザーにエラーが報告されません。  
  
 一時 PE サポートを活用するカスタム ツールは、次の規則に従う必要があります。  
  
-   `GeneratesDesignTimeSource` レジストリで 1 に設定する必要があります。  
  
     プログラム実行可能ファイルのコンパイルには、この設定がない場所はありません。  
  
-   生成されたコードは、グローバル プロジェクト設定と同じ言語でなければなりません。  
  
     要求された拡張機能として、カスタム ツールのレポートに関係なく一時 PE がコンパイルされる<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>される`GeneratesDesignTimeSource`がレジストリ内の 1 に設定します。 拡張子が .vb、.cs、または .jsl; を指定する必要はありません。任意の拡張機能があります。  
  
-   カスタム ツールによって生成されたコードを有効にする必要があり、時に、プロジェクトに存在する参照のセットのみを使用して、独自にコンパイルする必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>の実行が終了します。  
  
     一時 PE がコンパイルされると、コンパイラに提供される唯一のソース ファイルは、カスタム ツールの出力を示します。 そのため、一時 PE を使用するカスタム ツールは、プロジェクト内の他のファイルとは別にコンパイルできる出力ファイルを生成する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [BuildManager オブジェクトの概要](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [単一ファイル ジェネレーターの実装](../../extensibility/internals/implementing-single-file-generators.md)   
 [プロジェクトの既定の Namespace を決定します。](../../misc/determining-the-default-namespace-of-a-project.md)   
 [単一ファイル ジェネレーターの登録](../../extensibility/internals/registering-single-file-generators.md)

