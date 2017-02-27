---
title: "[ビルドの詳細設定] ダイアログ ボックス (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesAdvancedCompile"
helpviewer_keywords: 
  - "[ビルドの詳細設定] ダイアログ ボックス"
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# [ビルドの詳細設定] ダイアログ ボックス (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクトの詳細ビルド構成プロパティを指定するには、**プロジェクト デザイナー**の **\[ビルドの詳細設定\]** ダイアログ ボックスを使用します。  このダイアログ ボックスは、Visual Basic プロジェクトでのみ使用できます。  
  
### このダイアログ ボックスを表示するには  
  
1.  **\[ソリューション エクスプローラー\]** で、プロジェクト ノード \(ない **\[ソリューション\]** ノード\) を選択します。  
  
2.  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  **プロジェクト デザイナー**が表示されたら、**\[コンパイル\]** タブをクリックします。  
  
3.  [\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](../Topic/Compile%20Page,%20Project%20Designer%20\(Visual%20Basic\).md) で、**\[構成\]** と **\[プラットフォーム\]** を選択します。  簡易ビルド構成では、**\[構成\]** および **\[プラットフォーム\]** の一覧は表示されません。  詳細については、「[Debug and Release Project Configurations](http://msdn.microsoft.com/ja-jp/0440b300-0614-4511-901a-105b771b236e)」を参照してください。  
  
4.  **\[詳細コンパイル オプション\]** をクリックします。  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## 最適化  
 次のオプションは最適化を指定するもので、プログラムの小型化、プログラムの高速化、またはビルド プロセスの短縮を実現できる場合があります。  
  
 **\[整数オーバーフローのチェックを解除\]**  
 既定では、このチェック ボックスは整数のオーバーフロー チェックを有効にするには、をオフにします。  整数のオーバーフロー チェックを削除するには、このチェック ボックスをオンにします。  このチェック ボックスをオンにすると、整数の計算は高速場合があります。  ただし、オーバーフロー チェックを削除する場合は、データ型の空きオーバーフローすると、誤った結果が発生するエラーなしで格納される場合があります。  
  
 オーバーフロー状態と整数演算のオーバーフローがオンの場合、<xref:System.OverflowException> 例外がスローされます。  オーバーフロー状態がチェック アウトされていない場合、整数演算のオーバーフローは例外をスローしません。  
  
 **\[最適化を有効にする\]**  
 既定ではオフに設定され、コンパイラの最適化は無効です。  コンパイラの最適化を有効にするには、このチェック ボックスをオンにします。  コンパイラを最適化すると、出力ファイルのサイズが小さくなり、動作が速くなり、処理の効率が向上します。  ただし、最適化によって出力ファイル内のコードを再配置するため、コンパイラの最適化はデバッグを困難になります。  
  
 **\[DLL ベース アドレス\]**  
 このテキスト ボックスには、既定の DLL ベース アドレスが 16 進形式で表示されます。  クラス ライブラリ プロジェクトおよびコントロール ライブラリ プロジェクトでは、このテキスト ボックスを使用して、DLL 作成時に使用されるベース アドレスを指定できます。  
  
 **\[デバッグ情報を作成\]**  
 リストの **\[None\]**、**\[Full\]**、または **\[pdb\-only\]** をクリックします。  **\[None\]** を指定すると、デバッグ情報が生成されません。  **\[Full\]** の場合は、完全なデバッグ情報が生成され、**\[pdb\-only\]** の場合は、PDB デバッグ情報だけが生成されます。  既定では、このオプションは **\[Full\]** に設定されます。  
  
## コンパイル定数  
 条件付きコンパイル定数はソース ファイルに [\#Const](/dotnet/visual-basic/language-reference/directives/const-directive) のプリプロセッサ ディレクティブを使用するのと同様の動作をしますが、定義された定数は public で、プロジェクトのすべてのファイルに適用されます。  [\#If… Then… \#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) ディレクティブとともに、ソース ファイルを条件付きでコンパイルに条件付きコンパイル定数を使用できます。  「[Conditional Compilation](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation)」を参照してください。  
  
 **\[DEBUG 定数の定義\]**  
 既定ではオンになり、DEBUG 定数が設定されます。  
  
 **\[TRACE 定数の定義\]**  
 既定ではオンになり、TRACE 定数が設定されます。  
  
 **\[カスタム定数\]**  
 このテキスト ボックスには、アプリケーションのカスタム定数を入力します。  エントリはコンマで区切り、「Name1\="Value1",Name2\="Value2",Name3\="Value3"」のような形式で入力します。  
  
## 他の設定  
 **\[シリアル化アセンブリの生成\]**  
 コンパイラが XML シリアル化アセンブリを作成するかどうかを指定します。  コード内で型をシリアル化するために <xref:System.Xml.Serialization.XmlSerializer> クラスを使用している場合は、シリアル化アセンブリによってそのクラスの起動効率を改善できます。  既定では、このオプションは **\[自動\]** に設定されています。これは、コード内の型を XML にエンコードするために <xref:System.Xml.Serialization.XmlSerializer> を使用している場合にのみシリアル化アセンブリを生成することを指定します。  **\[オフ\]** は、コードで <xref:System.Xml.Serialization.XmlSerializer> を使用するかどうかに関係なく、シリアル化アセンブリを生成しないことを指定します。  **\[オン\]** の場合、シリアル化アセンブリが必ず生成されます。  シリアル化アセンブリには、`TypeName`.XmlSerializers.dll のように名前が付けられます。  
  
## 参照  
 [\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](../Topic/Compile%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)