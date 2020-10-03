  save() {
    const newData = this._data();
    return new Promise(res => {
      this.storage.set(newData, () => {
        console.log(`Saved data as`, newData);
        res();
      });
    });
  }

  async reset() {
    this.id = { id: 0 };
    this.tabs = {};
    this.tabConnections = [];
    this.tabUpdated = {};
    this.favicons = {};
    await this.save();
  }
