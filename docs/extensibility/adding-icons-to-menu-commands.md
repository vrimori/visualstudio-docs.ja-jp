---
title: メニュー コマンドにアイコンを追加する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8591c55a176493ace23df2de61ba26d58a3155e2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098393"
---
# <a name="adding-icons-to-menu-commands"></a>メニュー コマンドにアイコンを追加します。
コマンドは、メニューとツールバーの両方に表示できます。 ツールバー、アイコンとテキストの両方を使用するコマンドが通常表示されるだけアイコン (領域を節約する) ときにメニューに表示するコマンドの一般的なです。  
  
 アイコンは 16 ピクセル × 16 ピクセルと、8 ビット色深度 (256 色) または 32 ビット色深度 (true 色) のいずれかを指定できます。 32 ビット カラー アイコンはお勧めします。 アイコンを複数のビットマップが許可されていますが、通常水平方向の単一行に 1 つのビットマップに配置されます。 このビットマップは、ビットマップ内で使用可能な個別のアイコンと共に .vsct ファイルで宣言されています。 リファレンスを参照して、[ビットマップ要素](../extensibility/bitmaps-element.md)詳細についてはします。  
  
## <a name="adding-an-icon-to-a-command"></a>コマンドにアイコンを追加します。  
 次の手順では、メニュー コマンドを使用して既存の VSPackage プロジェクトがあることを前提としています。 これを行う方法を調べるを参照してください。[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
1.  32 ビットの色深度をビットマップを作成します。 アイコンは、常に 16 ピクセルの倍数で 16 x 16 のため、このビットマップは 16 ピクセルである必要があります。  
  
     各アイコンは、1 つの行で相互の横にあるビットマップに配置されます。 アルファ チャネルを使用して、各アイコンの透明度の場所を示します。  
  
     8 ビット色深度を使用する場合は、マゼンタを使用して`RGB(255,0,255)`、透過性とします。 ただし、32 ビット カラー アイコンはお勧めします。  
  
2.  アイコン ファイルを VSPackage プロジェクト内のリソース ディレクトリにコピーします。 ソリューション エクスプ ローラーで、アイコンをプロジェクトに追加します。 (リソースを選択し、コンテキスト メニューの 追加、既存の項目をクリックし、アイコン ファイルを選択します。)  
  
3.  エディターで .vsct ファイルを開きます。  
  
4.  追加、`GuidSymbol`の名前を持つ要素**testIcon**です。 GUID を作成する (**作成ツール/GUID**選択してから、**レジストリ形式**コピー をクリック) に貼り付けると、`value`属性。 結果は、次のようになります。  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  追加、`<IDSymbol>`アイコン。 `name`属性は、アイコンの ID、および`value`存在する場合、ストリップ上での位置を示します。 1 つのアイコンがある場合は、1 を追加します。 結果は、次のようになります。  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  作成、`<Bitmap>`で、`<Bitmaps>`を表す、ビットマップ、アイコンを含む、.vsct ファイルのセクションです。  
  
    -   設定、`guid`値の名前を`<GuidSymbol>`要素の前の手順で作成します。  
  
    -   設定、`href`ビットマップ ファイルの相対パスの値 (ここでは**リソース\\< アイコン ファイル名\>** です。  
  
    -   設定、`usedList`先ほど作成した IDSymbol する値。 この属性は、VSPackage で使用されるアイコンのコンマ区切りの一覧を指定します。 一覧に表示されないのアイコンは、除外されたフォーム コンパイルです。  
  
         ビットマップのブロックは、次のようになります。  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  既存の`<Button>`要素、設定、`Icon`先ほど作成した GUIDSymbol と IDSymbol の値を要素。 これらの値を持つボタン要素の例を次に示します。  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  アイコンをテストします。 プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスのコマンドを検索します。 追加したアイコンが表示にする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)   
 [VSCT XML スキーマ リファレンス](../extensibility/vsct-xml-schema-reference.md)