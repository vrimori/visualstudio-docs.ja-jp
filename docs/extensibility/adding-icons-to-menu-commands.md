---
title: メニュー コマンドへのアイコンの追加 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7856015fff4f62fb1f95ba791be34295717c439f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55003059"
---
# <a name="add-icons-to-menu-commands"></a>メニュー コマンドにアイコンを追加します。
コマンドは、メニューおよびツールバーの両方に表示できます。 ツールバーでは、通常、アイコンとテキストの両方で、コマンドが表示されますだけをアイコンで (スペースを節約) 中にメニューに表示されるコマンドの一般的です。  
  
 アイコンは 16 ピクセル × 16 ピクセルと 8 ビット色深度 (256 色) または 32 ビットの色深度 (true color) のいずれかを指定できます。 32 ビット カラー アイコンは、適しています。 アイコンは通常 1 つのビットマップの水平方向の行を 1 つで配置されますが、複数のビットマップが許可されます。 このビットマップがで宣言されている、 *.vsct*と共にビットマップ内で使用可能な個々 のアイコン ファイル。 リファレンスをご覧ください、 [Bitmaps 要素](../extensibility/bitmaps-element.md)の詳細。  
  
## <a name="add-an-icon-to-a-command"></a>コマンドにアイコンを追加します。  
 次の手順では、メニュー コマンドを使用して既存の VSPackage プロジェクトがあることを前提としています。 これを行う方法についてを参照してください。[メニュー コマンドを使用して拡張機能を作成する](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
1.  32 ビットの色深度のビットマップを作成します。 アイコンは、常に 16 ピクセルの倍数で 16 x 16 のため、このビットマップは 16 ピクセルである必要があります。  
  
     各アイコンは、互いの横にあるビットマップを 1 つの行に配置されます。 アルファ チャネルを使用して、各アイコンでの透過性の場所を示します。  
  
     8 ビット色を使用する場合は、マゼンタを使用して`RGB(255,0,255)`、透過性とします。 ただし、32 ビット カラー アイコンが優先されます。  
  
2.  アイコン ファイルのコピー、*リソース*VSPackage プロジェクトのディレクトリ。 **ソリューション エクスプ ローラー**アイコンをプロジェクトに追加します。 (選択**リソース**、コンテキスト メニューをクリックし**追加**、し**既存項目の**、アイコン ファイルを選択します)。  
  
3.  開く、 *.vsct*エディターでファイル。  
  
4.  追加、`GuidSymbol`の名前を持つ要素**testIcon**します。 GUID を作成する (**ツール** > **GUID の作成**を選択し、**レジストリ形式**クリック**コピー**)、に貼り付けます`value`属性。 このよう、結果になります。  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  追加、`<IDSymbol>`アイコン。 `name`属性は、アイコンの ID、および`value`存在する場合、ストリップ上での位置を示します。 1 つのアイコンがある場合は、1 を追加します。 このよう、結果になります。  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  作成、`<Bitmap>`で、`<Bitmaps>`のセクション、 *.vsct*を表す、ビットマップ、アイコンを含むファイル。  
  
    -   設定、`guid`値の名前に、`<GuidSymbol>`前の手順で作成した要素。  
  
    -   設定、`href`ビットマップ ファイルの相対パスに値 (この場合**リソース\\< アイコンのファイル名\>** します。  
  
    -   設定、`usedList`前に作成した IDSymbol する値。 この属性は、VSPackage で使用されるアイコンのコンマ区切りの一覧を指定します。 アイコンは、一覧にないは、除外されたフォームのコンパイルです。  
  
         このようビットマップ ブロックになります。  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  既存の`<Button>`要素、設定、`Icon`要素を前に作成した GUIDSymbol と IDSymbol の値。 これらの値を持つボタン要素の例を次に示します。  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  アイコンをテストします。 プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスでは、コマンドを検索します。 追加したアイコンを表示にする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)   
 [VSCT XML スキーマ リファレンス](../extensibility/vsct-xml-schema-reference.md)