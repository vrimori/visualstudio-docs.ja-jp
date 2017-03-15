---
title: "ビジュアル デザイナーで型を公開します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ビジュアル デザイナーに公開する型 [Visual Studio SDK]"
  - "型を公開するデザイナー [Visual Studio SDK]"
  - "カスタム ツール、ビジュアル デザイナーで型を公開します。"
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# ビジュアル デザイナーで型を公開します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] はデザイン時にビジュアル デザイナーを表示するにはクラスへのアクセスおよび typedef が必要です。  クラスは現在のプロジェクト \(その依存関係と参照\) の完全な依存関係のセットを含むアセンブリの定義済みセットから読み込まれます。  カスタム ツールで生成されたファイルで定義されている型とクラスにアクセスするビジュアル デザイナーが必要な場合もあります。  
  
 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] と  [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] プロジェクト システムは一時的なポータブル実行可能ファイル \(一時的な PE ファイル\) を使用して生成されたクラスおよび型へのアクセスもサポートします。  型がそれらのアセンブリから読み込まれデザイナーに表示されるようにカスタム ツールで生成されたファイルは一時アセンブリにコンパイルできます。  各カスタム ツールの出力は別の一時的な PE ファイルにコンパイルし生成されたファイルをコンパイルできるかどうかをこの一時コンパイルの成功または失敗はよって異なります。  プロジェクト全体がとしてビルドかどうかにかかわらず個々の一時的な PE ファイルはデザイナーで使用できる場合があります。  
  
 プロジェクト システムがカスタム ツールの出力ファイルへの変更を追跡するためにこれらの変更がカスタム ツールの実行結果は完全にサポートされています。  カスタム ツールが実行されるたびに新しい一時的な PE ファイルが生成され適切な通知はデザイナーに送信されます。  
  
> [!NOTE]
>  一時的なプログラムの実行可能ファイルの生成がバックグラウンドで行われるためエラーはユーザーにコンパイルが失敗した場合は報告されません。  
  
 一時的な PE ファイルのサポートを利用するカスタム ツールは次の規則に従う必要があります :  
  
-   `GeneratesDesignTimeSource` はレジストリの 1 に設定されている必要があります。  
  
     プログラムの実行可能ファイルをコンパイルしこの設定を使用せずにはなりません。  
  
-   生成されたコードはグローバルなプロジェクト設定と同じ言語で記述する必要があります。  
  
     一時的な PE ファイルは `GeneratesDesignTimeSource` がレジストリの 1 に設定するとカスタム ツールが <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> の要求された拡張機能として報告するために関係なくコンパイルします。  拡張子は .cs.vb.jsl である必要はありません ; これはの拡張です。  
  
-   カスタム ツールで生成されたコードが有効であるプロジェクトの発生時に <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> の参照の現在の設定だけを使用して実行が終了すると手動でコンパイルする必要があります。  
  
     一時的な PE ファイルをコンパイルするとコンパイラで提供されているソース ファイルはカスタム ツールの出力があります。  したがって一時的な PE ファイルを使用するカスタム ツールでもプロジェクト内の他のファイルとは無関係にコンパイルできる出力ファイルを生成する必要があります。  
  
## 参照  
 [Introduction to the BuildManager Object](http://msdn.microsoft.com/ja-jp/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [単一ファイル ジェネレーターの実装](../../extensibility/internals/implementing-single-file-generators.md)   
 [プロジェクトの既定の名前空間の決定](../../misc/determining-the-default-namespace-of-a-project.md)   
 [単一ファイル ジェネレーターを登録します。](../../extensibility/internals/registering-single-file-generators.md)