# Contributing

## Hazırlık
> Bu proje, Katkıcı Sözleşmesi'nde (Contributor Covenant) [code of conduct](./CODE_OF_CONDUCT.md) geçen davranış kurallarını takip etmektedir. Bu projeye katılarak, bu kurallara uymayı kabul etmiş olursunuz.

Öncelikle projenin [yakut-ui](https://github.com/tubitak-bilgem-yte/yakut-ui) GitHub sayfasında yer alan `fork` butonuna tıklayarak repository'yi fork yapın.

Sonrasında kendi hesabınıza fork yaptığınız repository'i bilgisayarınıza clone yapın.

```sh
git clone git@github.com:GITHUB_KULLANICI_ADI/yakut-ui.git
```

Clone işlemi tamamlandığı zaman projenin bulunduğu dizine giderek [yakut-ui](https://github.com/tubitak-bilgem-yte/yakut-ui) projesini Ana Kaynak (`upstream`) olarak ekleyin.

```sh
cd yakut-ui
git remote add upstream git@github.com:tubitak-bilgem-yte/yakut-ui.git
```

## Geliştirme için Çalışma Ortamını Hazırlama

Projenin hazırlık işlemleri tamamlandıktan sonra bilgisayarınızda Node 22 sürümüne sahip olduğunuzdan emin olun. Sonrasında geliştirmeye başlayabilmek için aşağıdaki komutu çalıştırın.

```sh
pnpm install
```

Bu komut projenin ihtiyaç duyduğu bağımlılıkları indirip kuracaktır.

## Değişikliklerin Yapılması

İlk olarak projenize ana kaynaktan `pull` alarak projenizin güncel olduğundan emin olun. Sonrasında değişikliklerinizi yapacağınız branch'i oluşturabilirsiniz.

```sh
git checkout master
git pull upstream master --rebase
git checkout -b my-awesome-fix
```

### Linting

Commitler commit öncesinde husky'nin precommit hook'u ile lint yapılır, lint hatası olan kodlar commitlenemez. Bunun önüne geçmek, geliştirme sürecini daha verimli hale getirmek amacıyla ESLint eklentisi olan bir IDE veya editör kullanmanız önerilir. Tüm popüler editörler için eklentiler mevcuttur. Commit öncesinde lint script'ini kendinizde çalıştırabilirsiniz.
```sh
pnpm check
```

### Testlerin Çalıştırılması

Testler 3 farklı tarayıcıda (`firefox`, `chromium`, `webkit`) çalışmaktadır.

Tek bir tarayıcı ortamında testleri çalıştırmak için;
```sh
pnpm test:<TARAYICI_ADI> // expl: pnpm test:webkit
```
Tüm tarayıcılarda testleri çalıştırmak için;
```sh
pnpm test
```
CI/CD ortamında olduğu gibi testleri çalıştırmak için;
```sh
pnpm test:ci
```

### Creating a Changeset

If you made changes for which you want to trigger a release, you need to create a changeset.
This documents your intent to release and allows you to specify a message that will be put into the changelog(s) of the package(s).

[More information on changesets](https://github.com/atlassian/changesets)

To create a changeset, run:

```sh
npx changeset
```

Use the menu to select for which packages you need a release, and then select what kind of release. For the release type, we follow [Semantic Versioning](https://semver.org/), so please take a look if you're unfamiliar.

In short:

- A documentation change or similar chore usually does not require a release
- A bugfix requires a patch
- A new feature (feat) requires a minor
- A breaking change requires a major

Exceptions:

- For alpha (<1.0.0), bugfixes and feats are both patches, and breaking changes are allowed as minors.
- For release-candidate and other special cases, other rules may follow.

## Değişikliklerin Commit Yapılması

Commit mesajları [conventional commit format](https://www.conventionalcommits.org/en/v1.0.0/) sayfasında ifade edilen format ile uyumlu olmalıdır.

```sh
fix(testing): fix terrible bug
```

## Pull Request Oluşturma

Yaptığınız değişiklikleri commit yaptıktan sonra branch'inize push yapabilirsiniz.

```sh
git push -u origin my-awesome-fix
```

Değişiklikleri başarılı bir şekilde push yaptıktan sonra kendi GitHub sayfanızdaki fork yapılmış proje sayfanızı açın. Sayfada yapmış olduğunuz değişikliklerin [yakut-ui](https://github.com/tubitak-bilgem-yte/yakut-ui) projesi ile birleşmesi için `Pull Request` oluşturacak bir buton yer alacaktır.
