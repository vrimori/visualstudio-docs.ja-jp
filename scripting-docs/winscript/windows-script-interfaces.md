---
title: "Windows スクリプト インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Windows スクリプト インターフェイス
Microsoft Windows のスクリプトのインターフェイスは、スクリプトを記述し、OLE オートメーション アプリケーションを追加する方法を提供します。  Windows のスクリプトに依存するスクリプト ホストはコンポーネント間でのスクリプトの実行の管理に複数のソースおよび販売元からスクリプト エンジンを使用できます。  スクリプト自体の言語、構文、永続的なファイル形式、実行モデルの実装は、スクリプトの販売元に、をオン任せられ。  
  
 Windows のスクリプト ドキュメントは、次のセクションに分かれています:  
  
 [Windows スクリプト ホスト](../winscript/windows-script-hosts.md)  
  
 [Windows スクリプト エンジン](../winscript/windows-script-engines.md)  
  
 [アクティブ スクリプトのデバッグの概要](../winscript/active-script-debugging-overview.md)  
  
 [アクティブ スクリプト プロファイリングの概要](../winscript/active-script-profiling-overview.md)  
  
 [Windows スクリプト インターフェイスのリファレンス](../winscript/reference/windows-script-interfaces-reference.md)  
  
## Windows スクリプトのバックグラウンド  
 Windows スクリプトのインターフェイスは 2 種類に分類されます: Windows スクリプトのホストは、エンジンと Windows スクリプトの作成。  ホストは、エンジンのスクリプトを実行するスクリプト エンジンと呼び出しを作成します。  Windows スクリプトのホストの例は次のとおりです。:  
  
-   Microsoft Internet Explorer  
  
-   インターネット ツールの作成  
  
-   Shell  
  
 Windows のスクリプト エンジンは、言語またはランタイム環境で開発することができます。次のものが含まれています:  
  
-   Microsoft Visual Basic Scripting Edition \(VBScript\)  
  
-   Perl  
  
-   Lisp  
  
 ホストの実装を行うには、できる限り柔軟で、Windows のスクリプトの OLE オートメーションのラッパーが用意されています。  ただし、Windows のスクリプトを直接使用している場合は、スクリプト エンジンをインスタンス化するには、このラッパー オブジェクトを使用してホストにランタイムの名前空間、永続化モデルのコントロールの度合いが、などありません。  
  
 Windows スクリプトのデザインは \(ブラウザーやビューアーなどのホスト nonauthoring ように編集環境でのみ必要なインターフェイス要素を分離すると、スクリプト エンジン \(VBScript\) 軽量保持できます。  
  
## Windows スクリプトの基本アーキテクチャ  
 次の図は、Windows スクリプトのホストと Windows スクリプト エンジンの間の相互作用を示します。  
  
 エンジンとホストの間の相互作用に関する手順は次の一覧に示します。  
  
1.  プロジェクトを作成します。  ホストは、プロジェクトまたはドキュメントを読み込みます。  この手順は、Windows のスクリプトに固有では、期すために、ここに含まれます。\)  
  
2.  Windows のスクリプト エンジンを作成します。  使用する特定のスクリプト エンジンのクラス ID \(CLSID\) を指定する新しいウィンドウのスクリプト エンジンを作成するホストでは `CoCreateInstance`。  たとえば、Internet Explorer の HTML ブラウザーは、HTML の \<OBJECT\> のタグの CLSID\= の属性でスクリプト エンジンのクラス ID を受け取ります。  
  
3.  スクリプトを読み込みます。  スクリプトの内容が保持されている場合、ホストは、スクリプトのストレージ、ストリーム、またはプロパティ バッグにするために、スクリプト エンジンの `IPersist*::Load` のメソッドを呼び出します。  それ以外の場合は、ホストは `IPersist*::InitNew` または null のスクリプトを作成するには [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) のメソッドを使用します。  スクリプト エンジンにスクリプトのテキストに与えるためにテキストが [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) を使用できるようにスクリプトを保持する `IActiveScriptParse::InitNew`を呼び出した後に、ホスト。  
  
4.  名前付きの項目を追加します。  スクリプト エンジンの名前空間にインポートそれぞれのトップレベルの項目の名前には、\(ページとフォームなど\) ホストは、エンジンの名前空間のエントリを作成するには [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) のメソッドを呼び出します。  この手順では、名前付きのトップレベルの項目が既に手順 3.で読み込まれたスクリプトの永続的な状態の一部である場合は必要ではありません。  ホストは中段で、項目を追加するには `IActiveScript::AddNamedItem` を使用しません \(HTML ページのコントロールなど\) ; なく、エンジンは、ホストの `ITypeInfo` と `IDispatch` のインターフェイスを使用して間接的にトップレベルの項目から中段の項目を取得します。  
  
5.  スクリプトを実行します。  ホストは、エンジンは [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) のメソッドの SCRIPTSTATE\_CONNECTED のフラグを設定してスクリプトの実行が開始します。  この呼び出しは `main()` のスクリプト化された関数と同様の方法で、スクリプト エンジンのアーキテクチャ工事を、イベント \(下記参照\) にしたり、コードを実行する静的な束縛が実行されます。  
  
6.  項目の情報を取得します。  スクリプト エンジンはトップレベルの項目とシンボルを関連付ける必要があるたびに特定の項目に関する情報を返す [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) のメソッドを呼び出します。  
  
7.  イベントをフックする。  実際のスクリプトを開始する前に、スクリプト エンジンは `IConnectionPoint` のインターフェイスを通じて関連するすべてのオブジェクトのイベントに接続します。  
  
8.  プロパティとメソッドを呼び出します。  スクリプトが実行されると、スクリプト エンジンは `IDispatch::Invoke` またはそのほかの標準 OLE データ バインディング機構を通じてメソッドへの参照と名前付きオブジェクトのプロパティを実現します。  
  
## Windows スクリプトの用語  
 このリストは、このドキュメントで使用するスクリプトを記述し、関連する用語の定義が含まれます。  
  
|語句|定義|  
|--------|--------|  
|オブジェクトをコード。|Visual Basic のフォームの分離モジュールなど、名前付きの項目、または名前付き項目に関連付けられた C \+\+.のクラスに関連付けられたスクリプト エンジンによって作成されたインスタンス。  できれば、サポート、OLE オートメーションのホストまたはそのほかの非スクリプトのエンティティが、コード オブジェクトを処理できる OLE のコンポーネント オブジェクト モデルの \(COM\) のオブジェクトです。|  
|の項目|OLE COM オブジェクト \(ホストがスクリプトに興味深く、OLE オートメーションをサポートする場合は 1\)。  この例には、Web ブラウザーに HTML ページとブラウザー、および Microsoft Word 文書およびダイアログ含まれます。|  
|スクリプト|スクリプト エンジンが実行するプログラムを構成するデータ。  スクリプトは `pcode`のテキスト、ブロック、またはマシン固有の実行可能コード バイトの部分が含まれている連続的な実行可能なデータである場合もあります。  ホストは `IPersist*` のインターフェイスの 1 回または [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) のインターフェイスを通じてスクリプト エンジンにスクリプトを読み込みます。|  
|スクリプト エンジン|スクリプトを処理する OLE オブジェクト。  スクリプト エンジンは [IActiveScript](../winscript/reference/iactivescript.md) と、オプションで、[IActiveScriptParse](../winscript/reference/iactivescriptparse.md) のインターフェイスを実装します。|  
|スクリプト ホスト|Windows のスクリプト エンジンを所有するプログラムまたはアプリケーション。  ホストは [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) と、オプションで、[IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md) のインターフェイスを実装します。|  
|スクリプトレット|取得するスクリプトの部分は [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) のインターフェイスを通じてオブジェクトにアタッチします。  スクリプトレットの集計コレクションは、スクリプトです。|  
|スクリプト言語|スクリプト \(VBScript など\)、その言語のセマンティクス記述される言語。|  
  
## 参照  
 [Windows Script Interfaces](../winscript/windows-script-interfaces.md)