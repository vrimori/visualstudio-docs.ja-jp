---
title: "メニュー コマンドにアイコンを追加します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ツールバーへの追加アイコン [Visual Studio]"
  - "ツールバー [Visual Studio] アイコンをコマンドに追加します。"
  - "コマンド [Visual Studio] アイコンを追加します。"
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# メニュー コマンドにアイコンを追加します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コマンドは、メニューとツールバーの両方に表示できます。 ツールバーのアイコンとテキストの両方によってコマンドが通常表示されるだけをアイコンで \(スペースを節約\) 中にメニューに表示されるコマンドの一般的なです。  
  
 アイコンは、幅 16 ピクセル、高さ 16 ピクセルで 8 ビット色深度 \(256 色\) または 32 ビットの色深度 \(true color\) を指定できます。 32 ビット カラー アイコンは、優先的に使用します。 通常、アイコンは複数ビットマップが許可されていますが、1 つのビットマップに 1 つの行内に配置されます。 このビットマップは、ビットマップ内で使用できる個々 のアイコンと共に .vsct ファイルで宣言されています。 について、参照、 [ビットマップ要素](../extensibility/bitmaps-element.md) 詳細です。  
  
## コマンドにアイコンを追加します。  
 次の手順では、メニュー コマンドを使用して既存の VSPackage プロジェクトであると想定します。 これを行う方法については、次を参照してください。 [メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
1.  32 ビットの色深度を持つビットマップを作成します。 アイコンは、常に 16 ピクセルの倍数で 16 x 16 のため、このビットマップは 16 ピクセルである必要があります。  
  
     各アイコンは、単一の行で相互の横にあるビットマップに配置されます。 アルファ チャネルを使用して、各アイコンの透明度の場所を示します。  
  
     8 ビット色を使用する場合は、マゼンタを使用して `RGB(255,0,255)`, 、透過性とします。 ただし、32 ビット カラー アイコンは、優先的に使用します。  
  
2.  アイコン ファイルを VSPackage プロジェクトにリソース ディレクトリにコピーします。 ソリューション エクスプ ローラーで、アイコンをプロジェクトに追加します。 \(リソースを選択し、コンテキスト メニューの \[追加\]、\[既存の項目をクリックしておよびアイコン ファイルを選択します。\)  
  
3.  .Vsct ファイル エディターで開きます。  
  
4.  追加、 `GuidSymbol` の名前を持つ要素 **testIcon**します。 GUID を作成する \(**ツール\/作成 GUID**, 選択してから、 **レジストリ形式** コピー\] をクリック\) に貼り付けます、 `value` 属性です。 結果は、次のようになります。  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  追加、 `<IDSymbol>` アイコン。`name` 属性は、アイコンの ID と `value` 存在する場合、ストリップ上での位置を示します。 1 つのアイコンがある場合は、1 を追加します。 結果は、次のようになります。  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  作成、 `<Bitmap>` で、 `<Bitmaps>` 、アイコンを含むビットマップを表す .vsct ファイルのセクションです。  
  
    -   設定、 `guid` 値の名前に、 `<GuidSymbol>` 、前の手順で作成した要素です。  
  
    -   設定、 `href` 値をビットマップ ファイルの相対パス \(この場合 **リソース\] \\ \< アイコン ファイル名 \>**します。  
  
    -   設定、 `usedList` 前に作成した IDSymbol する値。 この属性は、VSPackage で使用されるアイコンのコンマ区切りの一覧を指定します。 一覧にないアイコンは、除外されたフォーム コンパイルです。  
  
         ビットマップのブロックは、次のようになります。  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  既存の `<Button>` 要素、設定、 `Icon` 前に作成した GUIDSymbol と IDSymbol の値を要素。 これらの値を持つボタン要素の例を次に示します。  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  自分のアイコンをテストします。 プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスで、コマンドを検索します。 追加したアイコンが表示されます。  
  
## 参照  
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)   
 [VSCT XML スキーマ リファレンス](../extensibility/vsct-xml-schema-reference.md)