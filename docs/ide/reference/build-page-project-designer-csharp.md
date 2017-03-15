---
title: "[ビルド] ページ (プロジェクト デザイナー) (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
caps.latest.revision: 43
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: a2cd0d3a9f964136e971f3709b5eacc9600832d0
ms.lasthandoff: 02/22/2017

---
# <a name="build-page-project-designer-c"></a>[ビルド] ページ (プロジェクト デザイナー) (C#)
**プロジェクト デザイナー**の **[ビルド]** ページでは、プロジェクトのビルド構成プロパティを指定します。 このページは、[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] プロジェクトにのみ適用されます。  
  
 **[ビルド]** ページにアクセスするには、**ソリューション エクスプローラー**のプロジェクト ノード (**[ソリューション]** ノードではありません) を選択します。 その後、メニュー バーで **[プロジェクト]**、**[プロパティ]** の順に選択します。 プロジェクト デザイナーが表示されたら、**[ビルド]** タブをクリックします。  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="configuration-and-platform"></a>構成およびプラットフォーム  
 次のオプションを使用すると、表示または変更する構成およびプラットフォームを選択できます。  
  
> [!NOTE]
>  簡易ビルド構成を使用した場合、デバッグ バージョンとリリース バージョンのどちらをビルドするかの決定はプロジェクト システムによって行われます。 したがって、これらのオプションは表示されません。 詳細については、「[デバッグ構成およびリリース プロジェクト構成](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)」を参照してください。  
  
 **構成**  
 表示または変更する構成設定を指定します。 この設定は、**[アクティブ (Debug)]** (既定)、**[Debug]**、**[Release]**、または **[すべての構成]** に指定できます。  
  
 **プラットフォーム**  
 表示または変更するプラットフォーム設定を指定します。 既定の設定は **[アクティブ (Any CPU)]** です。 アクティブなプラットフォームは、**構成マネージャー**を使って変更できます。 詳細については、「[How to: Create and Edit Configurations](../../ide/how-to-create-and-edit-configurations.md)」(方法 : 構成を作成および編集する) を参照してください。  
  
## <a name="general"></a>全般  
 次のオプションでは、いくつかの C# コンパイラ設定を構成できます。  
  
 **条件付きコンパイル シンボル**  
 条件付きコンパイルを実行するシンボルを指定します。 シンボルはセミコロン (";") で区切ります。 詳しくは、「[/define (C# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option)」をご覧ください。  
  
 **定数 DEBUG の定義**  
 DEBUG をアプリケーションのすべてのソース コード ファイル内のシンボルとして定義します。 これを選択することは、`/define:DEBUG` コマンド ライン オプションを使用することと同じです。  
  
 **定数 TRACE の定義**  
 TRACE をアプリケーションのすべてのソース コード ファイル内のシンボルとして定義します。 これを選択することは、`/define:TRACE` コマンド ライン オプションを使用することと同じです。  
  
 **対象の CPU**  
 出力ファイルがターゲットとするプロセッサを指定します。 32 ビット Intel 互換プロセッサの場合は **[x86]** を、64 ビット Intel 互換プロセッサの場合は **[x64]** を、ARM プロセッサの場合は **[ARM]** をそれぞれ選択します。または、どのプロセッサでもかまわないことを指定する場合は、**[Any CPU]** を選択します。 **[Any CPU]** はプロジェクトの既定の値であり、さまざまなハードウェアでアプリケーションを実行できるようにします。  
  
 詳しくは、「[/platform (C# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)」をご覧ください。  
  
 **32 ビットを優先**  
 **[32 ビットの優先]** チェック ボックスがオンの場合、アプリケーションは、Windows の 32 ビット バージョンおよび 64 ビット バージョンで 32 ビット アプリケーションとして実行されます。 このチェック ボックスがオフの場合、アプリケーションは、Windows の 32 ビット バージョンで 32 ビット アプリケーションとして、および Windows の 64 ビット バージョンで 64 ビット アプリケーションとしてそれぞれ実行されます。  
  
 アプリケーションを 64 ビット アプリケーションとして実行する場合は、ポインター サイズが 2 倍になり、32 ビットのみの他のライブラリとの互換性の問題が発生する可能性があります。 4 GB 以上のメモリが必要な場合、または 64 ビットにするとパフォーマンスが大幅に向上する場合にのみ、64 ビット アプリケーションを実行すると便利です。  
  
 このチェック ボックスは、次の条件がすべて満たされた場合にのみ利用できます。  
  
-   **[ビルド]** ページの **[プラットフォーム ターゲット]** ボックスの一覧で、**[Any CPU]** が設定されている。  
  
-   **[アプリケーション]** ページの **[出力の種類]** ボックスの一覧で、プロジェクトがアプリケーションであることが指定されている。  
  
-   **[アプリケーション]** ページの **[ターゲット フレームワーク]** ボックスの一覧で、.NET Framework 4.5 が指定されている。  
  
 **アンセーフ コードの許可**  
 [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) キーワードを使用するコードをコンパイルできるようにします。 詳しくは、「[/unsafe (C# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option)」をご覧ください。  
  
 **コードの最適化**  
 コンパイラで実行する最適化を有効または無効にします。最適化を実行すると、出力ファイルのサイズが小さくなり、速度と効率が向上します。 詳しくは、「[/optimize (C# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option)」をご覧ください。  
  
## <a name="errors-and-warnings"></a>エラーと警告  
 ビルド処理におけるエラーおよび警告のオプションの構成には、次の設定が使用されます。  
  
 **警告レベル**  
 コンパイラの警告を表示するレベルを指定します。 詳しくは、「[/warn (C# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option)」をご覧ください。  
  
 **警告の表示なし**  
 1 つ以上の警告について、警告を生成するコンパイラの機能を無効にします。 警告番号が複数ある場合は、コンマまたはセミコロンで区切ります。 詳しくは、「[/nowarn (C# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option)」をご覧ください。  
  
## <a name="treat-warnings-as-errors"></a>[警告をエラーとして扱う]  
 エラーとして扱う警告を指定するには、次の設定が使用されます。 ビルドが警告を検出したときに、どのような状況でエラーを返すのかを、次のいずれかのオプションを選択して指定します。 詳しくは、「[/warnaserror (C# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)」をご覧ください。  
  
 **None**  
 警告をエラーとして扱いません。  
  
 **[特定の警告]**  
 指定した警告をエラーとして扱います。 警告番号が複数ある場合は、コンマまたはセミコロンで区切ります。  
  
 **All**  
 すべての警告をエラーとして扱います。  
  
## <a name="output"></a>出力  
 次の設定は、ビルド処理の出力オプションを構成するために使用します。  
  
 **出力パス**  
 このプロジェクト構成の出力ファイルの場所を指定します。 このボックスにビルド出力のパスを入力するか、**[参照]** をクリックし、パスを指定します。 このパスは、相対パスであることに注意してください。絶対パスを入力しても、相対パスとして保存されます。 既定のパスは bin\Debug または bin\Release\\ です。 詳細については、「[デバッグ構成およびリリース プロジェクト構成](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)」を参照してください。  
  
 簡易ビルド構成を使用した場合、デバッグ バージョンとリリース バージョンのどちらをビルドするかの決定はプロジェクト システムによって行われます。 **[デバッグ]** メニューの **[ビルド]** コマンド (F5) を使用すると、指定した **[出力パス]** に関係なく、デバッグ用の場所にビルドが配置されます。 ただし、**[ビルド]** メニューの **[ビルド]** コマンドでは、指定した場所にビルドが配置されます。 詳細については、「[デバッグ構成およびリリース プロジェクト構成](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)」を参照してください。  
  
 **XML ドキュメント ファイル**  
 ドキュメントのコメントを処理するファイルの名前を指定します。 詳しくは、「[/doc (C# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option)」をご覧ください。  
  
 **COM の相互運用機能に登録**  
 マネージ アプリケーションにより、COM オブジェクトがマネージ アプリケーションとやり取りできるようにする COM オブジェクト (COM 呼び出し可能ラッパー) が公開されることを示します。 **[COM 相互運用機能の登録]** プロパティを使用できるようにするには、このアプリケーションの**プロジェクト デザイナー**の [[アプリケーション]](../../ide/reference/application-page-project-designer-visual-basic.md) ページで **[出力の種類]** プロパティを **[クラス ライブラリ]** に設定する必要があります。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] アプリケーションに追加して、COM オブジェクトとして公開するクラスの例については、「[Example COM Class](/dotnet/csharp/programming-guide/interop/example-com-class)」(COM クラスの例) を参照してください。  
  
 **シリアル化アセンブリの生成**  
 コンパイラが XML シリアライザー ジェネレーター ツール (Sgen.exe) を使用して XML シリアル化アセンブリを作成するかどうかを指定します。 コード内で型をシリアル化するために <xref:System.Xml.Serialization.XmlSerializer> クラスを使用している場合は、シリアル化アセンブリによってそのクラスの起動効率を改善できます。 既定では、このオプションは **[自動]** に設定されています。これは、コード内の型を XML にエンコードするために <xref:System.Xml.Serialization.XmlSerializer> を使用している場合にのみシリアル化アセンブリを生成することを指定します。 **[オフ]** は、コードで <xref:System.Xml.Serialization.XmlSerializer> を使用するかどうかに関係なく、シリアル化アセンブリを生成しないことを指定します。 **[オン]** の場合、シリアル化アセンブリが必ず生成されます。 シリアル化アセンブリには、`TypeName`.XmlSerializers.dll のように名前が付けられます。 詳細については、「[XML シリアライザー ジェネレーター ツール (Sgen.exe)](http://msdn.microsoft.com/Library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6)」を参照してください。  
  
 **詳細設定**  
 クリックすると、[[ビルドの詳細設定] ダイアログ ボックス (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) ダイアログ ボックスが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトのプロパティのリファレンス](../../ide/reference/project-properties-reference.md)   
 [C# コンパイラ オプション](/dotnet/csharp/language-reference/compiler-options/index)
