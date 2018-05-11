---
title: 'チュートリアル: エディターの拡張機能とショートカット キーを使用する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f8f8a310832f0691b4bc4056baddeb1fbbad78f8
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>チュートリアル: エディターの拡張機能とショートカット キーを使用します。
エディター拡張機能で、ショートカット キーに応答することができます。 次のチュートリアルでは、テキスト ビューにショートカット キーを使用してビューの表示要素を追加する方法を示します。 このチュートリアルは、ビューポート装飾エディター テンプレートに基づいておりを使用して表示要素を追加することができます、プラス記号です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) プロジェクトの作成  
  
1.  C# の場合は、VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を付けます`KeyBindingTest`です。  
  
2.  エディターのテキスト装飾項目テンプレートをプロジェクトに追加し、名前を付けます`KeyBindingTest`です。 詳細については、次を参照してください。[エディター項目テンプレートに、拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  次の参照を追加し、設定**CopyLocal**に`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 KeyBindingTest クラス ファイルでは、PurpleCornerBox にクラス名を変更します。 左側の余白に電球が表示されますを使用して、その他の適切な変更を行います。 コンス トラクター内からレイヤーを表示要素の名前を変更する**KeyBindingTest**に**PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  

KeyBindingTestTextViewCreationListener.cs クラス ファイルでから AdornmentLayer の名前変更**KeyBindingTest**に**PurpleCornerBox**:
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  

## <a name="handling-typechar-command"></a>TYPECHAR コマンドの処理
Visual Studio 2017 バージョン 15.6 エディターの拡張機能でのコマンドを処理する唯一の方法を実装する前に、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンド フィルターに基づいています。 Visual Studio 2017 15.6 のバージョンでは、エディター コマンドのハンドラーに基づく、最新の簡略化されたアプローチが導入されました。 次の 2 つのセクションでは、旧バージョンと最新のアプローチの両方を使用してコマンドを処理する方法を示します。

## <a name="defining-the-command-filter-prior-to-visual-studio-2017-version-156"></a>(Visual Studio 2017 バージョン 15.6) より前のコマンドのフィルターを定義します。

 コマンドのフィルターの実装は、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>、表示要素をインスタンス化して、コマンドを処理します。  
  
1.  クラス ファイルを追加し、名前を付けます`KeyBindingCommandFilter`です。  
  
2.  次の using ステートメントを追加します。  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  KeyBindingCommandFilter をという名前のクラスを継承する必要があります<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>です。  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  コマンドのチェーン、およびコマンド フィルターは既に追加されているかどうかを表すフラグでテキスト ビューのプライベート フィールドを次のコマンドを追加します。  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  テキスト ビューを設定するコンス トラクターを追加します。  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  実装、`QueryStatus()`メソッドを次のようにします。  
  
    ```csharp  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  実装、`Exec()`場合をビューに紫色のボックスを追加するためのメソッド、文字が入力されたとします。  
  
    ```csharp  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## <a name="adding-the-command-filter-prior-to-visual-studio-2017-version-156"></a>(Visual Studio 2017 バージョン 15.6) より前のコマンドのフィルターを追加します。
 装飾プロバイダーは、テキスト ビューにコマンドのフィルターを追加する必要があります。 この例では、プロバイダーを実装する<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>テキスト ビューの作成イベントをリッスンするようにします。 この表示要素のプロバイダーでは、表示要素の Z オーダーを定義する装飾層をエクスポートします。  
  
1.  次のコードを追加、KeyBindingTestTextViewCreationListener ファイルでステートメントを使用します。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2.  テキスト ビュー アダプターを取得するには、インポートする必要があります、<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>です。  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
3.  変更、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>メソッドが追加されますので、`KeyBindingCommandFilter`です。  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
4.  `AddCommandFilter`ハンドラーは、テキスト ビュー アダプターを取得し、コマンドのフィルターを追加します。  
  
    ```csharp  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>(Visual Studio 2017 15.6 のバージョンで開始) コマンド ハンドラーを実装します。

最初に、API の最新のエディターを参照するプロジェクトの Nuget の参照を更新します。

1. クリックし、プロジェクトを右クリックして**Nuget パッケージの管理**です。

2. **Nuget Package Manager**を選択、**更新**] タブで、[、**パッケージをすべて選択**] チェック ボックスし、[**更新**です。

実装は、コマンド ハンドラーが<xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>、表示要素をインスタンス化して、コマンドを処理します。  
  
1.  クラス ファイルを追加し、名前を付けます`KeyBindingCommandHandler`です。  
  
2.  次の using ステートメントを追加します。  
  
    ```csharp  
    using Microsoft.VisualStudio.Commanding;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
    using Microsoft.VisualStudio.Utilities;
    using System.ComponentModel.Composition;   
    ```  
  
3.  KeyBindingCommandHandler をという名前のクラスを継承する必要があります`ICommandHandler<TypeCharCommandArgs>`、およびエクスポートとして<xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:
  
    ```csharp  
    [Export(typeof(ICommandHandler))]
    [ContentType("text")]
    [Name("KeyBindingTest")]
    internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>  
    ```  
  
4.  コマンド ハンドラーの表示名を追加します。  
  
    ```csharp  
    public string DisplayName => "KeyBindingTest";
    ```  
    
5.  実装、`GetCommandState()`メソッドを次のようにします。 このコマンド ハンドラーは、コア エディター TYPECHAR コマンドを処理するため、コア エディター コマンドの有効化を委任することができます。
  
    ```csharp  
    public CommandState GetCommandState(TypeCharCommandArgs args)
    {
        return CommandState.Unspecified;
    } 
    ```  
  
6.  実装、`ExecuteCommand()`場合をビューに紫色のボックスを追加するためのメソッド、文字が入力されたとします。 
  
    ```csharp  
    public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
    {
        if (args.TypedChar == '+')
        {
            bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
                "KeyBindingTextAdorned", out bool adorned) && adorned;
            if (!alreadyAdorned)
            {
                new PurpleCornerBox((IWpfTextView)args.TextView);
                args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
            }
        }

        return false;
    }
    ```  
 7. KeyBindingTestTextViewCreationListener.cs ファイルから、KeyBindingCommandHandler.cs に装飾層の定義をコピーし、KeyBindingTestTextViewCreationListener.cs ファイルを削除します。
 
    ```csharp  
    /// <summary>
    /// Defines the adornment layer for the adornment. This layer is ordered
    /// after the selection layer in the Z-order.
    /// </summary>
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("PurpleCornerBox")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    private AdornmentLayerDefinition editorAdornmentLayer;    
    ```  

## <a name="making-the-adornment-appear-on-every-line"></a>表示要素を行うすべての行に表示されます  

すべての文字で表示されていた元の表示要素の ' a' をテキスト ファイルにします。 行にのみ表示要素を追加するので、'+' の文字への応答の表示要素を追加するコードを変更しましたが、ここで、'+' は型指定されています。 1 回以上表示要素が表示されるように、装飾コードを変更できますすべて 'a' です。  
  
KeyBindingTest.cs ファイルでは、'a' 文字の装飾にビューのすべての行を反復処理する CreateVisuals() メソッドを変更します。  
  
```csharp  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
  
1.  KeyBindingTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
2.  作成またはテキスト ファイルを開きます。 文字を含む一部の単語の入力 '、' し、入力 + テキスト ビューで任意の場所。  
  
     紫色の四角形は、ファイルの 'a' すべての文字に表示されます。
